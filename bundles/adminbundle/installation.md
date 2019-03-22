# Chapter 1. Installation

## Install bundle

We assume you’re familiar with [Composer](https://getcomposer.org), a dependency manager for PHP. Use the following command to add the bundle to your **composer.json** and download the package.

```bash
composer require harmony/admin-bundle
```

> Alternatively, you can clone the [https://github.com/harmonycms/admin-bundle](https://github.com/harmonycms/admin-bundle) repository.

## Configure security layer

To secure the admin interface, you will need to update your security layer and restrict his access for administrators only. Edit the `config/packages/security.yaml` file and add the next configuration:

{% code-tabs %}
{% code-tabs-item title="config/packages/security.yaml" %}
```yaml
security:
    access_control:
        - { path: ^/admin, roles: ROLE_ADMIN }
```
{% endcode-tabs-item %}
{% endcode-tabs %}

