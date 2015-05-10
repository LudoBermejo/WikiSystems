Custom Posts don't add themselves in authors page. To do so, you need to add a function in functions theme to do so. 


Function in functions.php
```php
function cuentos_author_archive( &$query )
{
    if ( $query->is_author )
        $query->set( 'post_type', 'cuentos' );
    remove_action( 'pre_get_posts', 'custom_post_author_archive' ); // run once!
}
add_action( 'pre_get_posts', 'cuentos_author_archive' );

```
