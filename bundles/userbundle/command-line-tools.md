# Chapter 4. Command Line Tools

This bundle provides a number of command line utilities to help manage HarmonyCMS users.  
Commands are available for the following tasks:

* [Create a User](command-line-tools.md#create-a-user)
* [Promote a User](command-line-tools.md#promote-a-user)

## Create a User

You can use the `user:create` command to create a new user for your application. The command takes three arguments, the `username`, `email`, and `password` for the user you are creating.

For example if you wanted to create a user with username `testuser`, with email `test@example.com` and password `p@ssword`, you would run the command as follows.

```bash
php bin/console fos:user:create testuser test@example.com p@ssword
```

If any of the required arguments are not passed to the command, an interactive prompt will ask you to enter them. For example, if you ran the command as follows, then you would be prompted to enter the `email` and `password` for the user you want to create.

```bash
php bin/console fos:user:create testuser
```

Specifying the `--super-admin` option will flag the user as a super admin when the user is created. A super admin has access to any part of your application. An example is provided below:

```bash
php bin/console fos:user:create adminuser --super-admin
```

## Promote a User

The `user:promote` command enables you to add a role to a user or make the user a super administrator.

If you would like to add a role to a user you simply pass the `username` of the user as the first argument to the command and the `role` to add to the user as the second.

```bash
php bin/console fos:user:promote testuser ROLE_ADMIN
```

{% hint style="danger" %}
Changes will not be applied until the user **logs out** and back in again.
{% endhint %}

