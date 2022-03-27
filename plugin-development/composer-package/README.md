# Composer Package For Auto loading files of a folder.

URL to download composer: [Composer Official](https://getcomposer.org/download/)

### Instructions:

- Download the composer exe file for Windows
- Install in your computer, done.
- Restart the ide if it is open
- Go to command line/ integrated terminal of IDE, write `composer` & hit enter

### Configuration:

- Navigate to the plugin folder where you want to install, using command line
- Write and execute `composer init`
- Write package name, format - ( Vendor Name \ Package Name), e.g - arafatjamil01\plugin-name
- Description should describe what the app is about
- Author, if matched, skip it, type n, or simply hit enter
- Minimum stability, write `dev`
- Package type `wordpress-plugin`, this is a dedicated type.
- License should be according to your version of license. e.g - GPLv3
- If you don't have any dependencies, or dev dependency, hit no for both cases
- If the namespace matches your package name defined before, hit yes for namespace, or hit no.

This will create a `composer.json` file in the directory, there you should write the custom configurations for all your files.

After `"require":{}` configuration, write the following configuration

```json
    "autoload": {
        "psr-4": {
            "Themx\\Core\\": "includes/"
        },
        "files": []
    }
```
In the above code, Themx\Core is the namespace of the plugin. Includes is the folder which will contain contents with different names. 

After settings these up. Write & execute command `composer install`.

A `vendor` folder is created, with a file `autoload.php` and a folder named `composer` is created.

### Including composer in our project.

At the top of our plugin, we will need to write the following code, after the plugin definition, i.e - adding the `autoload.php` file, right after checking if `ABSPATH` is defined.

```php
defined( 'ABSPATH' ) || exit;

require_once __DIR__.'/vendor/autoload.php';
```

### Writing contents within the includes file

We can have many folders within `includes` folder, the same folder we defined in `"psr-4"` configuration in `composer.json`. We need to follow the `"psr-4"` structure to write the names of the 
folder and files. The first letter should be capital letter and the rest should be small letters. e.g - Admin, Cli, Frontend etc.

The name of the files should also follow similar structure. e.g - We can create a file in Admin folder named `Menu.php`.

### Writing proper namespace

If we are in the `includes` folder, the namespace should be `Themx\Core`. And if we are in the `includes\Admin` folder, the namespace of `Menu.php` will be `Themx\Core\Admin`.
