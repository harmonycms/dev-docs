# Decoupled from object mapping

One of the main idea of HarmonyCMS is to be fully decoupled from any object mapping system.  
By doing that, HarmonyCMS is able to provide full support of **SQL** and **No-SQL** databases.

### Supporting both or only one object mapping system

When you are developing a bundle or an extension for HarmonyCMS, keep in mind that you need to be fully decoupled from any object mapping system.

#### Supporting both systems

```text
{
  "require": {
    "doctrine/implementation": "1.0"
  }
}
```

{% hint style="info" %}
This means, the end user will be able to chose between SQL and No-SQL databases.  
It will need to require `emulienfou/orm-pack` or `emulienfou/mongodb-pack` packages.
{% endhint %}

#### Supporting ORM only

```text
{
  "require": {
    "doctrine/orm-implementation": "1.0"
  }
}
```

#### Supporting MongoDB only

```text
{
  "require": {
    "doctrine/mongodb-implementation": "1.0"
  }
}
```

