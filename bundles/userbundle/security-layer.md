# Chapter 3. Security layer

To be able to perform some action \(login and register\), you will need to configure the Symfony security layer.

Edit the `config/packages/security.yaml` file and add the appropriate blocks/rules as shown below, in this minimal configuration example.

{% code-tabs %}
{% code-tabs-item title="config/packages/security.yaml" %}
```yaml
security:
    encoders:
        Symfony\Component\Security\Core\User\UserInterface:
            algorithm: bcrypt

    role_hierarchy:
        ROLE_ADMIN:       ROLE_USER
        ROLE_SUPER_ADMIN: ROLE_ADMIN

    providers:
        user_provider:
            id: Harmony\Bundle\UserBundle\Security\UserProvider

    firewalls:
        dev:
            pattern: ^/(_(profiler|wdt)|css|images|js)/
            security: false

        main:
            pattern:  ^/
            provider: user_provider
            user_checker: Harmony\Bundle\UserBundle\Security\UserChecker
            anonymous:    true

            form_login:
                login_path: harmony_user_login
                check_path: harmony_user_login

            logout: true


    # Easy way to control access for large sections of your site
    # Note: Only the *first* access control that matches will be used
    access_control:
        - { path: ^/login, role: IS_AUTHENTICATED_ANONYMOUSLY }
        - { path: ^/password-reset, role: IS_AUTHENTICATED_ANONYMOUSLY }
        - { path: ^/lost-password, role: IS_AUTHENTICATED_ANONYMOUSLY }

```
{% endcode-tabs-item %}
{% endcode-tabs %}

