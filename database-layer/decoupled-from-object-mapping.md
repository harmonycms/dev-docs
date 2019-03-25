# Decoupled from object mapping

One of the main idea of HarmonyCMS is to be fully decoupled from any object mapping system.  
By doing that, HarmonyCMS is able to provide full support of **SQL** and **No-SQL** databases \(ORM / ODM\). When you are developing a bundle or an extension for HarmonyCMS, keep in mind that you need to be fully decoupled from any object mapping system.

Since Symfony 4, Symfony provide **Packs** who are time savers. By example, when using `symfony/orm-pack` it is a great way to get the most commonly needed Doctrine related packages and bundles for ORM support.  
However, nether `symfony/odm-pack` or `symfony/mongodb-pack` currently exists to commonly install all related packages for MongoDB.

This is why I currently provide two Symfony Packs, `emulienfou/orm-pack` and `emulienfou/mongodb-pack`. This packs have the particularity to provides each 2 virtual packages to be used to specify which doctrine implementation is supported by the bundle or extension.

## Supporting both systems

If your bundle or extension is supporting both ORM and ODM databases systems, you should require the next virtual package:

```text
{
  "require": {
    "doctrine/implementation": "1.0"
  }
}
```

{% hint style="info" %}
This means, the end user will be able to chose between SQL and No-SQL databases.  
It will need to install `emulienfou/orm-pack` or `emulienfou/mongodb-pack` packages.
{% endhint %}

## Supporting ORM only

If you choose to support ORM only, you should require the next virtual package:

```text
{
  "require": {
    "doctrine/orm-implementation": "1.0"
  }
}
```

{% hint style="info" %}
This means, the end user will need to install `emulienfou/orm-pack`package.
{% endhint %}

## Supporting MongoDB only

If you choose to support ODM only, you should require the next virtual package:

```text
{
  "require": {
    "doctrine/mongodb-implementation": "1.0"
  }
}
```

{% hint style="info" %}
This means, the end user will need to install `emulienfou/mongodb-pack`package.
{% endhint %}

