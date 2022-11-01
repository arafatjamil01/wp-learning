# Creating first submenu with a different name

```php
$parent_slug = 'themexplosion';
$capability  = 'manage_options';

add_menu_page( __( 'Themexplosion', 'aj' ), __( 'Themexplosion', 'aj' ), $capability, $parent_slug, [ $this, 'home' ], 'dashicons-welcome-learn-more' );

add_submenu_page( $parent_slug, __( 'Home', 'aj' ), __( 'Home', 'aj' ), $capability, $parent_slug, [ $this, 'home' ] );

add_submenu_page( $parent_slug, __( 'About', 'aj' ), __( 'Settings', 'aj' ), $capability, 'tx-about', [ $this, 'settings_page' ] );
```

Here I have setup an admin menu page and two submenu pages. The first submenu page contains the exact parent slug and the exact callback function as the parent one. This will create the first submenu with a different name.

```php
[ $this, 'function_name' ]
```
Calls the function in OOP Model, if you are using procedural model, directly use the function name.