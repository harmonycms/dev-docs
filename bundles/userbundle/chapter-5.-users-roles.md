# Chapter 5. User's roles

## UserRoleType

The user role form type class provide a new form type class who list all available roles from `security.role_hierarchy.roles`.

### Use in form builder

This new form type class can be used like:

```php
use Harmony\Bundle\UserBundle\Form\Type\UserRoleType;

$builder->add('roles', UserRoleType::class);
```

### Use in admin config

Example to add a property `roles` with the custom type to get list of all roles:

```yaml
- { property: 'roles', type: Harmony\Bundle\UserBundle\Form\Type\UserRoleType }
```

