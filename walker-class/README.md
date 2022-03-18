# Walker Class

`Walker class` provides different structures for WordPress rendering. The navigation menu extends the walker class and called nav walker. Likewise, the comment walker class extends the walker class. 

Class location: `wp-includes` folder.

Code Reference: [WordPress Walker Class](https://developer.wordpress.org/reference/classes/walker/)

In this way, whenever there is any kind of hierarchy that needs to be maintained dynamically, wordpress users use walker class.

This class can be customized extending the main Walker Class by the user.

## Nav Walker

`Nav Walker` is walker for navigation. 

Code Reference: [Walker Nav Menu](https://developer.wordpress.org/reference/classes/walker_nav_menu/)

`wp_nav_menu()` function renders the navigation menu. The output is considered by the walker menu in the following way - 

```html
<div class="menu-container">
    <ul> <!-- Start Level start_lvl()  -->
        <li><a href="#"> <!-- Start Element start_el()  -->
            
            Link</a></li> <!-- End Element end_el()  -->
    </ul> <!-- End Level end_lvl()  -->
</div>
```