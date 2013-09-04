# cpt-tax-post-permalinks #

**Contributors:** daankortenbach  
**Donate link:** https://www.gittip.com/daankortenbach/  
**Tags:** cpt, taxonomy, permalink, rewrite  
**Requires at least:** 3.6  
**Tested up to:** 3.6  
**Stable tag:** 0.1  
**License:** GNU General Public License v2.0 (or later)  
**License URI:** http://www.opensource.org/licenses/gpl-license.php  

## Description ##

A class for WordPress to allow permalink structures bases on /custom-post-type/taxonomy-term/post-slug/

## Installation ##

1. Upload `cpt-tax-post-permalinks` to the `/wp-content/plugins/` directory
1. Activate the plugin through the 'Plugins' menu in WordPress

Example usage:

```php
if ( class_exists( 'FS_CPT_Tax_Post_Permalinks' ) ) {

    $fs_cpt = new FS_CPT_Tax_Post_Permalinks();

    $fs_cpt_labels = array(
        'name'                => _x( 'Events', 'post type general name' ),
        'singular_name'       => _x( 'Event', 'post type singular name' )
    );

    $fs_cpt_args = array(
        'post_type'           => 'fs_event',
        'labels'              => $fs_cpt_labels,
        'supports'            => array( 'title', 'editor', 'thumbnail', 'excerpt' ),
        'rewrite'             => array(
            'slug'            => 'events/%event_type%',
            'with_front'      => false
        ),
        'has_archive'         => 'events'
    );

    $fs_cpt->add_cpt( $fs_cpt_args );

    $fs_tax_args = array(
        'taxonomy'        => 'event_type',
        'post_type'       => 'fs_event',
        'label'           => 'Types',
        'singular_label'  => 'Type',
        'hierarchical'    => true,
        'query_var'       => true,
        'rewrite'         => array( 'slug' => 'events' )
    );
    $fs_cpt->add_tax( $fs_tax_args );

    $fs_permalink_args = array(
        'taxonomy'        => 'event_type'
    );
    $fs_cpt->add_permalink( $fs_permalink_args );
}
```

## Changelog ##

### 0.1 ###
* Initial version.
