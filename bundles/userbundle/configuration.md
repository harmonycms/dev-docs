# Chapter 2. Configuration

## User class

Fully Qualified Domain Name \(FQDN\) of the user class.  
Can be an interface, model or entity/document class.

```yaml
harmony_user:
    user_class: Symfony\Component\Security\Core\User\UserInterface
```

## Password reset

### Email from

Sender of the password reset requests.

```yaml
harmony_user:
    password_reset:
        email_from: john.doe@gmail.com
```

### Token TTL

TTL of a password reset request \(seconds\).

```yaml
harmony_user:
    password_reset:
        token_ttl: 7200
```

