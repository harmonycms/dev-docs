# Chapter 5. Providers

Settings can be pulled from multiple sources. Currently, the bundle comes with 5 settings providers. They can be configured and prioritized. **If a setting with the same name will come from &gt;1 providers, setting from provider with higher priority will override settings from lower priority providers**.

Settings providers:

* [Simple](providers.md#simple-settings-provider)
* [DoctrineODM](providers.md#doctrineodm-settings-provider)
* [DoctrineORM](providers.md#doctrineorm-settings-provider)
* [Cookie](providers.md#cookie-settings-provider)
* [AWS SSM](providers.md#aws-ssm-settings-provider)

And additional 2 decorating providers:

* [Phpredis](providers.md#phpredis-decorating-settings-provider)
* [Predis](providers.md#predis-decorating-settings-provider)

## Providers

### Simple settings provider

`Harmony\Bundle\SettingsManagerBundle\Provider\SimpleSettingsProvider`

This is a provider, which only holds settings collections. Currently, it's being used to hold settings from configuration, but many more can be configured.

To configure additional simple providers, factory is provided because provider can only accept already denormalized objects.

Configuration example:

```yaml
setting_provider_factory.foo:
    class: Harmony\Bundle\SettingsManagerBundle\Provider\Factory\SimpleSettingsProviderFactory
    arguments:
        $serializer: '@settings_manager.serializer'
        $normalizedData:
            -
                - name: foo
                  description: 'foo desc'
                  type: bool
                  domain: { name: default } 
                  data: { value: false }
                  tags: [{ name: 'super_switch' }]
    tags:
        - { name: settings_manager.provider_factory, provider: foo, priority: 10 }
```

### DoctrineODM settings provider

### DoctrineORM settings provider

`Harmony\Bundle\SettingsManagerBundle\Provider\DoctrineOrmSettingsProvider`

This is a provider which reads and saves settings using `EntityManagerInterface`.

Required libraries:

* [doctrine/orm](https://github.com/doctrine/doctrine2)
* [acelaya/doctrine-enum-type](https://github.com/acelaya/doctrine-enum-type)

  > I am guessing you already have it :open\_mouth:  
  > `composer require doctrine/orm acelaya/doctrine-enum-type`

Configuration example:

1. Doctrine configuration

{% code-tabs %}
{% code-tabs-item title="config/packages/doctrine.yaml" %}
```yaml

doctrine:
    orm:
        mappings:
            HarmonySettingsManagerBundle:
                type: yml
                is_bundle: true
                dir: "Resources/config/doctrine"
                alias: HarmonySettingsManagerBundle
                prefix: Harmony\Bundle\SettingsManagerBundle
```
{% endcode-tabs-item %}
{% endcode-tabs %}

1. Create setting entity

{% code-tabs %}
{% code-tabs-item title="App/Entity/Setting.php" %}
```php
<?php
declare(strict_types=1);

namespace App\Entity;

use Doctrine\ORM\Mapping as ORM;
use Harmony\Bundle\SettingsManagerBundle\Model\SettingModel;

/**
 * @ORM\Entity()
 * @ORM\Table(name="setting")
 */
class Setting extends SettingModel
{
    /**
     * @var int
     *
     * @ORM\Id
     * @ORM\GeneratedValue
     * @ORM\Column(type="integer")
     */
    protected $id;
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

1. Update your doctrine schema.
2. Register settings provider:

```yaml
Harmony\Bundle\SettingsManagerBundle\Provider\DoctrineOrmSettingsProvider:
    arguments:
        $entityManager: '@doctrine.orm.default_entity_manager'
        $settingsEntityClass: 'App\Entity\Setting'
    tags:
        - { name: settings_manager.provider, provider: orm, priority: 20 }
```

### Cookie settings provider

`Harmony\Bundle\SettingsManagerBundle\Provider\CookieSettingsProvider`

This is a provider, which only enables existing settings by using a cookie. Cookies are encoded, so that they could not be randomly enabled by users.

Required libraries:

* [paragonie/paseto](https://github.com/paragonie/paseto)

  > `composer require paragonie/paseto`

  `Paseto` is used to encrypt cookies.

  Configuration example:

```yaml
Harmony\Bundle\SettingsManagerBundle\Provider\CookieSettingsProvider:
    arguments:
        $serializer: '@settings_manager.serializer'
    tags:
        - { name: settings_manager.provider, provider: cookie, priority: 30 }
        - { name: kernel.event_subscriber }
```

### Asymmetric Cookie settings provider

`Harmony\Bundle\SettingsManagerBundle\Provider\AsymmetricCookieSettingsProvider`

This is a provider, which only enables existing settings by using a cookie. Cookies are encoded with asymmetric private and public keys, so that they could not be randomly enabled by users.

Required libraries:

* [paragonie/paseto](https://github.com/paragonie/paseto)

  > `composer require paragonie/paseto`

  `Paseto` is used to encrypt cookies.

  Configuration example:

```yaml
Harmony\Bundle\SettingsManagerBundle\Provider\AsymmetricCookieSettingsProvider:
    arguments:
        $serializer: '@settings_manager.serializer'
    tags:
        - { name: settings_manager.provider, provider: asymmetric_cookie, priority: 40 }
        - { name: kernel.event_subscriber }
```

### AWS SSM settings provider

`Harmony\Bundle\SettingsManagerBundle\Provider\AwsSsmSettingsProvider`

This is a provider, which is used only for reading and updating existing ssm parameters as settings.

Required libraries:

* [aws/aws-sdk-php](https://github.com/aws/aws-sdk-php)

  > `composer require aws/aws-sdk-php`

Configuration example:

```yaml
Harmony\Bundle\SettingsManagerBundle\Provider\AwsSsmSettingsProvider:
    arguments:
        - '@Aws\Ssm\SsmClient'
        - '@settings_manager.serializer'
        - ['amazing_parameter_name']
    tags:
        - { name: settings_manager.provider, provider: aws_ssm }
```

## Decorators

### Phpredis decorating settings provider

`Harmony\Bundle\SettingsManagerBundle\Provider\DecoratingRedisSettingsProvider`

This provider is used to cache other settings providers like DoctrineORM or AWS SSM. It uses Redis client, not [doctrine/cache providers](https://github.com/doctrine/cache) or [symfony/cache adapters](https://github.com/symfony/cache) because we want to take advantage of redis data structures for simplier invalidation process.

Required extensions:

* [phpredis](https://github.com/phpredis/phpredis)

  > `pecl install redis-3.1.6`

Configuration example:

```yaml
Harmony\Bundle\SettingsManagerBundle\Provider\DecoratingRedisSettingsProvider:
    decorates: 'Harmony\Bundle\SettingsManagerBundle\Provider\DoctrineOrmSettingsProvider'
    arguments:
        $decoratingProvider: 'Harmony\Bundle\SettingsManagerBundle\Provider\DecoratingRedisSettingsProvider.inner'
        $redis: '@settings.cache.redis' # you need to register your own \Redis client in container
        $serializer: '@settings_manager.serializer'
```

### Predis decorating settings provider

`Harmony\Bundle\SettingsManagerBundle\Provider\DecoratingPredisSettingsProvider`

Same as phpredis decorating settings provider It just replaces the phpredis extension with [predis](https://github.com/nrk/predis).

Required libraries:

* [predis/predis](https://github.com/nrk/predis)

  > `composer require predis/predis`

**Configuration reference**

```yaml
harmony_settings_manager:
    settings:
        -
            name: foo
            description: 'foo desc'
            domain: default # Used for grouping settings.
            type: bool
            data: false
            tags: [super_switch]
    profiler:
        enabled: false
    logger:
        enabled: false
        service_id: null # Psr\Log\LoggerInterface service id
    settings_files:
        # - '%kernel.root_dir%/config/extra_settings.yml'
```

