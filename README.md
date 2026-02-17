# Master-wordpress-actions-hooks
**Hooks: are generic term in wordpress that allow your plugin to hook into the rest of the WordPress, by calling your custom functions at specific times.**
## Types of hook
1. Actions
2. Filters

## Action is a php fiunction that is execuite at specific points throughout the WordPress core. Actions allows to run our code at a specific time when WordPress is doing something.
### Example 
1. Creating a widget when WordPress is initializing
2. Sending a tweet when someone publish a post

## Filters: allow us to get and modify WordPress data before it is sent to the database/browser, using our custom functiomns. Filters give us access to the data which we can modify and return that data back using our custom functions.
### Example
1. Customizing how excerpts are displayed
2. Modifying your site title before its displayed
### 1. Actions
a. do_actions() - executes our hooked functions

b. add_action() - hooks our custom functions

```
do_action($tag, $arg)

add_action($tag, $callback_function, $priority, $args_count)

function callback_function($arg) {
    // do stuff here
}
```
###  2. Filters
a. apply_filters() - executes our hooked functions

b. add_filter() - hooks our custom functions
```
$value = apply_filters($tag, $value, $arg)

add_filter($tag, $callback_func, $priority, $arg_count)

function callback_func($value, $arg) {
    // modify $value
    return $value;
}
```
### Show custom login error by filter
```
if ( ! empty( $errors ) ) {
    echo '<div id="login_error"> . apply_filters('login_errors', $errors) . </div>'
}
if ( ! function_exits('modify_login_error') ) {
    function modify_login_error() {
    $errors = 'Login unsuccessfull. Try again.'
    return $errors;
}
}
add_filter('login_errors', 'modify_login_error');
```
### Remove filter and Add own custom filter
```
if ( has_filter('the_content', 'custom_function_name' ) {
    remove_filter('the_content', 'custom_function_name');
    add_filter('the_content', 'my_custom_function_name');
}
```
### Register frontend enqueue style and script
```
if( ! function_exits('register_enque_style_script') ) {
    function register_enque_style_script() {

    }
}
add_action('wp_enqueue_scripts', 'register_enque_style_script');
```
### Register admin_register_enque_style_script
```
if( ! function_exits('admin_register_enque_style_script') ) {
    function admin_register_enque_style_script() {

    }
}
add_action('admin_enqueue_scripts', 'register_enque_style_script');
```
### Widget init action hook
```
if ( ! function_exits('function_name') ) {
    function function_name() {
        register_sidebar(array(
            'name' =>__(),
            'id'   => 'id',
            'description' => __(''),
            ) )
    }
}
add_action('widget_init', 'function_name')
```

### init action hook
```
fi ( ! function_exit('the_register_my_menus') ) {
    function the_register_my_menus() [
        register_nav_menu( array(
            'footer_menu' => __();
        ))
    ]
}
add_action('init', 'the_register_my_menus');
```
### Add menu page or sub menu page by admin menu action hook
```
if ( ! function_exist('register_your_plugin_menu') ) {
    function register_your_plugin_menu() {
	add_menu_page(
		__( 'Your Plugin', PLUGIN_DOMAIN ),
		'Your Plugin',
		PLUGIN_ROLE,
		PLUGIN_SLUG,
		false,
		'dashicons-admin-generic',
		''
	);

	add_submenu_page(
		PLUGIN_SLUG,
		'Your Plugin',
		'Dashboard',
		PLUGIN_ROLE,
		PLUGIN_SLUG,
		'your_plugin_dashboard_callback',
	);
}
}
add_action( 'admin_menu', 'register_your_plugin_menu', 9 );
```

### admin_init action hook for handle admin menu page access and it's call after admin_menu must
```
if ( ! function_exits('restrict_action') ) {
    function restrict_action() {
        if ( ! current_user_can('manage_options') && ( ! wp_doing_ajax()) ) {
            wp_die(__('message', 'textdomain') );
            wp_redirect( site_url('/student-dashboard') );
            exit;
        }
    }
}
add_action('admin_init', 'restrict_action', 1)