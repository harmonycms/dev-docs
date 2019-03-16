# Chapter 2. Console command

## Display raw configuration

You can execute the next command to display the current raw configuration for the extension alias `harmony_settings_manager`:

```bash
php bin/console debug:config harmony_settings_manager
```

{% hint style="warning" %}
Settings from **themes** or **extensions** won't be visible in the raw configuration
{% endhint %}

## Using the debug command

### Displays all available settings

```text
php bin/console debug:settings
```

### Display all configured domains

```text
php bin/console debug:settings --domains
```

### Display settings for a specific domain

```text
php bin/console debug:settings --domain=default
```

### Display all settings with a specific tag

```text
php bin/console debug:settings --tag=foo
```

