<?php
// Suleiman Shop Theme Functions
add_action('after_setup_theme', 'suleiman_shop_setup');
function suleiman_shop_setup() {
    add_theme_support('post-thumbnails');
    add_theme_support('woocommerce');
    add_theme_support('wc-product-gallery-zoom');
    add_theme_support('wc-product-gallery-lightbox');
    add_theme_support('wc-product-gallery-slider');
}

// Enqueue Styles and Scripts
add_action('wp_enqueue_scripts', 'suleiman_shop_scripts');
function suleiman_shop_scripts() {
    wp_enqueue_style('bootstrap', get_template_directory_uri() . '/assets/css/bootstrap.min.css');
    wp_enqueue_style('main-style', get_template_directory_uri() . '/assets/css/style.css');
    wp_enqueue_script('bootstrap', get_template_directory_uri() . '/assets/js/bootstrap.bundle.min.js', ['jquery'], null, true);
    wp_enqueue_script('custom-js', get_template_directory_uri() . '/assets/js/custom.js', ['jquery'], null, true);
    
    // Localize script for AJAX
    wp_localize_script('custom-js', 'ajax_object', [
        'ajax_url' => admin_url('admin-ajax.php'),
        'nonce' => wp_create_nonce('suleiman_shop_nonce')
    ]);
}
?>
