`spl_autoload_register` - A php function that helps to autoload all the files of a WordPress plugin. A very handy and speedy way instead of `include`, `require` etc for every single file.

### How it works

To reduce complexity, I always take a separate file called - `autoloader.php` in the plugin root directory and make this file required at the top of the pugin's main php file.

```php
require_once __DIR__ . '/autoloader.php';
```

Then I use the following code to make the autoloader working.

```php
spl_autoload_register( 'plugin_autoloader' );

function plugin_autoloader( $class ) {
 $path = __DIR__ . '/includes/' . str_replace( '\\', '/', $class ) . '.php';

 if ( file_exists( $path ) ) {
  include_once $path;
 }
}
```

The function `spl_autoload_register()` automatically loads everything, and must contain a callback function inside it.
e.g -
`spl_autoload_register( function( $class_name ) ) {}`

In the previous example, we have separated the function to keep things tidy. The names of the classes are always loaded as a parameter in the callback function, each class at a time.

Since auto loading works for all available classes in the ecosystem, we will limit the scope using folder names. This is where `$path` variable comes into play. Since we are in WordPress plugin, we will use `__DIR__` constant and I have kept all my functions in `includes` folder. This variable will load the classes from the files. To replace the backslashes from namespace into forward slash, I have used `str_replace` function to replace the backslashes.

I want the sub folders to autoload the classes as well, in that case, the name of the subfolder must match the namespace. It is the easiest practice to create the subfolder name, namespace, filename and class name, in small letters.

For example - I want to autoload load `admin/settings.php` file, then it's namespace must be `admin` and the name of the class must be `settings`. This seemed the easiest to me, even though this is not the only way. In other cases, you can modify your folder structure and do necessary operations to load features.

Since so many classes are loaded using this function, we simply put a check with `file_exists` function.If the file exists, only then it will start to include.

### Different namespacing

If you want to use different kind of namespace for your project. for example -

`namespace wphound\includes;`

The location of the file is in the `includes` folder. `wphound` is the name of the plugin. Now, to match the directory path of the file, we need to replace `wphound\` with `\`

```php
spl_autoload_register(
 function ( $class ) {
  $class_name = str_replace( 'wphound\\', '\\', $class );

  $path = __DIR__ . str_replace( '\\', '/', $class_name ) . '.php';

  if ( file_exists( $path ) ) {
   include_once $path;
  }
 }
);
```

In this case, the folder structure and the namespace must be same. For example, for `Admin.php`, namespace can be -  `wphound\includes`, then the class file should be in the 'includes` folder.

When creating object from the class, after the `new` keyword, the namespace must be called. For example - 
`$admin = new wphound\includes\Admin();`

In this way, the `includes` folder will be used, when calling `spl_autoload_register` functions. In this way, folder name can be changed, or folders can be nested.
