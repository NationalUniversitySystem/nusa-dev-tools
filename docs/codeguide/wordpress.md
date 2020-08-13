# Wordpress

## Code Development
### Hooks
There are two types of hooks in WordPress, filters and actions.
- "Filters" must return something. You are literally filtering an existing object, value, array, etc. It might be an empty string or array, but the filter and it's parameters will be passing something to it.
```php
/**
 * Manipulate or trigger code based on the context of the content.
 *
 * @param string $the_content The good old content of any WP object.
 */
add_filter( 'the_content', function( $the_content ) {
	// Alter the content, append something to the content, check for something via a global $post to trigger other code, etc.
	return $the_content;
}, 10, 1 );
```
- "Actions" do not return anything specific, can have returns to escape the function/method like in a return pattern.
```php
/**
 * Manipulate or trigger code based on the context of the content.
 */
add_action( 'wp_enqueue_scripts', function() {
	// Enqueue general theme styles
	wp_enqueue_style( 'national-university', get_template_directory_uri() . '/assets/css/theme.min.css', [], filemtime( get_template_directory() . '/assets/css/theme.min.css' ) );

	// Enqueue specific styles for a page.
	if ( is_page( 'campaign-name' ) ) {
		wp_enqueue_style( 'campaign-name-styles', get_template_directory_uri() . '/assets/css/campaign-name.min.css', [], filemtime( get_template_directory() . '/assets/css/campaign-name.min.css'; ) );
	}
}, 999 );
```
- Pay close attention to the priority and parameters when defining hooks (and the defaults).
	- The default priority is 10.
	- The default parameter number is 1.
	- If the defaults will be used, no need to declare them.
	- If a callback has more than 1 parameter you will need to define that in the hook declaration.
	```php
	// No deafult priority nor parameter used.
	add_filter( 'the_content', function( $the_content ) {
		return $the_content
	} );

	// Lower number in priority so it executes earlier than the standard "10" and declare the number of parameters.
	add_filter( 'wp_kses_allowed_html', function() {
		if ( 'post' === $context ) {
			$allowed['img']['data-src']  = true;
		}

		return $allowed;
	}, 5, 2 )
	```


---

## Admin side (content management)
### Images
- When uploading images, add _at least_ an `alt` value. This is for accessibility purposes and because we use the caption and/or alt values to display text on every image.
- Rename the files so they are easier to search for. Usually utilizing the image subject's name and activity.
	- Example: "louis g. in class room"
	- If you were not provided with the image subject's name, ask for it from the design team or find on [Photoshelter](https://natuniv.photoshelter.com/index).
	- Optimize the image through some of our online tools or Photoshop for web settings with 80-90 percent judging your best for un-noticeable pixelation.
