## How to get started with AJAX in WordPress

- use actions wp_ajax_(action_name_here) & wp_ajax_nopriv_(action_name_here) to initiate functions
- you can use the same or different functions for the same purpose
- then define the ajax js file, use jQuery if needed, wordpress has jquery inside already
- use 
```php 
 wp_localize_script( 'js_file_handle', 'name_of_object', [ 'key' => 'value' ]
 ```
- the key value pair can be given primarily the wordpress ajax url admin_url('admin-ajax.php')
- define the ajax action name in the jquery, exactly like the action name in wp_ajax_(action_name_here) hook.
- write the function as needed. e.g - beforeSend, success keys in jQuery or state change in vanilla JS
- according to the defined actions, wordPress should just work fine. 