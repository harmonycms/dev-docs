# Quick start

The settings bundle allow you to register new settings fro your website. To do so add a file named `config/packages/settings_manager.yaml`. Here is an example:

```yaml
helis_settings_manager:
    settings:
        - name: foo
          description: 'foo desc'
          type: bool
          data: false
          tags:
              - 'super_switch'

        - name: baz
          description: 'master toggle for awesome new feature'
          type: string
          data: fish
          tags:
              - 'experimental'
              - 'poo'
```

## Available types

Here is the list of all available types allowed by the settings bundle. You can use the **short name** or the **FQDN** name.

| Short name \(key\) | Fully qualified domain name \(FQDN\) |
| :--- | :--- |
| `birthday` | Symfony\Component\Form\Extension\Core\Type\BirthdayType |
| `bool` | Symfony\Component\Form\Extension\Core\Type\CheckboxType |
| `checkbox` | Symfony\Component\Form\Extension\Core\Type\CheckboxType |
| `choice` | Symfony\Component\Form\Extension\Core\Type\ChoiceType |
| `collection` | Symfony\Component\Form\Extension\Core\Type\CollectionType |
| `color` | Symfony\Component\Form\Extension\Core\Type\ColorType |
| `country` | Symfony\Component\Form\Extension\Core\Type\CountryType |
| `currency` | Symfony\Component\Form\Extension\Core\Type\CurrencyType |
| `datetime` | Symfony\Component\Form\Extension\Core\Type\DateTimeType |
| `date` | Symfony\Component\Form\Extension\Core\Type\DateType |
| `date_interval` | Symfony\Component\Form\Extension\Core\Type\DateIntervalType |
| `email` | Symfony\Component\Form\Extension\Core\Type\EmailType |
| `entity` | Symfony\Bridge\Doctrine\Form\Type\EntityType |
| `file` | Symfony\Component\Form\Extension\Core\Type\FileType |
| `float` | Symfony\Component\Form\Extension\Core\Type\NumberType |
| `int` | Symfony\Component\Form\Extension\Core\Type\IntegerType |
| `integer` | Symfony\Component\Form\Extension\Core\Type\IntegerType |
| `language` | Symfony\Component\Form\Extension\Core\Type\LanguageType |
| `locale` | Symfony\Component\Form\Extension\Core\Type\LocaleType |
| `money` | Symfony\Component\Form\Extension\Core\Type\MoneyType |
| `number` | Symfony\Component\Form\Extension\Core\Type\NumberType |
| `password` | Symfony\Component\Form\Extension\Core\Type\PasswordType |
| `percent` | Symfony\Component\Form\Extension\Core\Type\PercentType |
| `radio` | Symfony\Component\Form\Extension\Core\Type\RadioType |
| `range` | Symfony\Component\Form\Extension\Core\Type\RangeType |
| `repeated` | Symfony\Component\Form\Extension\Core\Type\RepeatedType |
| `string` | Symfony\Component\Form\Extension\Core\Type\TextType |
| `tel` | Symfony\Component\Form\Extension\Core\Type\TelType |
| `textarea` | Symfony\Component\Form\Extension\Core\Type\TextareaType |
| `text` | Symfony\Component\Form\Extension\Core\Type\TextType |
| `time` | Symfony\Component\Form\Extension\Core\Type\TimeType |
| `timezone` | Symfony\Component\Form\Extension\Core\Type\TimezoneType |
| `url` | Symfony\Component\Form\Extension\Core\Type\UrlType |
| `yaml` | Helis\SettingsManagerBundle\Form\Type\YamlType |

