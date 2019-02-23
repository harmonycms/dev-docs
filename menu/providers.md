# Chapter 4. Providers

By default KnpMenu and KnpMenuBundle are shipped with multiple providers:

* [ArrayAccessProvider](https://github.com/KnpLabs/KnpMenu/blob/master/src/Knp/Menu/Provider/ArrayAccessProvider.php) A menu provider getting the menus from a class implementing ArrayAccess.
* [LazyProvider](https://github.com/KnpLabs/KnpMenu/blob/master/src/Knp/Menu/Provider/LazyProvider.php) A menu provider building menus lazily thanks to builder callables.
* [PsrProvider](https://github.com/KnpLabs/KnpMenu/blob/master/src/Knp/Menu/Provider/PsrProvider.php) A menu provider getting the menus from a PSR-11 container.
* [BuilderAliasProvider](https://github.com/KnpLabs/KnpMenuBundle/blob/master/src/Provider/BuilderAliasProvider.php) A menu provider that allows for an AcmeBundle:Builder:mainMenu shortcut syntax
* [BuilderServiceProvider](https://github.com/KnpLabs/KnpMenuBundle/blob/master/src/Provider/BuilderServiceProvider.php) This provider uses methods of services to build menus.
* [ContainerAwareProvider](https://github.com/KnpLabs/KnpMenuBundle/blob/master/src/Provider/ContainerAwareProvider.php)

However, to simplify the creation and storage of menus, HarmonyCMS is shipped by default with one more provider: The Configuration provider.

## Configuration provider

## Database provider

