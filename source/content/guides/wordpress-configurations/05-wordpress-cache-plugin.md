---
title: WordPress Configurations Guide
subtitle: Pantheon WordPress Cache Plugin Configuration
description: Optimize WordPress and Varnish caching to maximize your site's performance.
tags: [cache, plugins]
contenttype: [guide]
innav: [false]
categories: [config]
cms: [wordpress]
audience: [development]
product: [--]
integration: [plugins]
permalink: docs/guides/wordpress-configurations/wordpress-cache-plugin
---

This section provides information on Pantheon's WordPress plugin.

Pantheon maintains an [optimized version of WordPress](https://github.com/pantheon-systems/WordPress) that includes a plugin to control cache expiration. By default, pages expire from the Varnish Edge Cache after 10 minutes (600 seconds). The plugin sets a default HTTP header: `Cache-Control: public, max-age=600`

## Clear Site Cache

You can clear the site cache manually or automatically.

- To clear the cache manually, click the **Clear Cache** button.

- To clear the cache automatically, refer to the [Pantheon Advanced Page Cache](https://wordpress.org/plugins/pantheon-advanced-page-cache) and follow the instructions.

## Pantheon Page Cache Plugin Configuration

### Increase the Default Time to Live Value

You can increase the default time to live value to improve the chances that a visitor will request a cached page. Cached page requests reduce page load times.

1. Log in to your WordPress site as an administrator.

1. Click **Settings**.

1. Click **Pantheon Cache**. You'll end up at: `/wp-admin/options-general.php?page=pantheon-cache`

1. Modify the **Default Cache Time**.

    You should strike a balance between freshness of content and speed. We recommend a minimum of 600 seconds. If you can increase the setting to 30 minutes (1800 seconds) or 1 hour (3600 seconds), many more requests will hit the Edge Cache. Every page served from the Edge Cache won't hit your application container's PHP workers or MySQL database, which means faster page load times and a better user experience for site visitors.

1. Click **Save Changes**.

![WordPress Pantheon Cache Plugin settings](../../../images/WordPress_Pantheon-Cache-Settings.png)

### Maintenance Mode

You can enable maintenance mode for others while working on your site.

1. Log in to your WordPress site as an administrator.

1. Click **Settings**.

1. Click **Pantheon Cache**. You'll end up at: `/wp-admin/options-general.php?page=pantheon-cache`

1. Modify the **Maintenance Mode**.

    A simple notice displays to users who request a page that is not already cached.
    `Briefly unavailable for scheduled maintenance. Check back in a minute.`

1. Click **Save Changes**.

## Use Pantheon Cache Functions Programmatically

There are three functions that are useful to developers within the [pantheon-page-cache.php](https://github.com/pantheon-systems/WordPress/blob/default/wp-content/mu-plugins/pantheon-mu-plugin/inc/pantheon-page-cache.php) file that houses the Pantheon Cache plugin code. You can call them from within your own custom code using various WordPress hooks, such as [save_post()](https://developer.wordpress.org/reference/hooks/save_post/). Currently, the [limit on the number of paths](https://github.com/pantheon-systems/WordPress/issues/24) that can be cleared in a single call is 10.

### flush_site

This function flushes the site cache for the entire site. This achieves the same result as the **Clear Site Cache** button on the Pantheon Cache administration page.

```php
/**
 * Clear the cache for the entire site.
 *
 * @return void
 */
public function flush_site()
```

### clean_post_cache

This function flushes the cache for an individual post, which is identified by the `$post_id`. The optional `$include_homepage` argument can also be passed. The default value is `true` if no value is set.

```php
/**
 * Clear the cache for a post.
 *
 * @param  int $post_id A post ID to clean.
 * @return void
 */
public function clean_post_cache( $post_id, $include_homepage = true )
```

### clean_term_cache

This function flushes the cache for an individual term or terms which are passed in an array, or for a complete taxonomy passed via a single taxonomy ID.

```php
/**
 * Clear the cache for a given term or terms and taxonomy.
 *
 * @param int|array $ids Single or list of Term IDs.
 * @param string $taxonomy Can be empty and will assume tt_ids, else will use for context.
 * @return void
 */
public function clean_term_cache( $term_ids, $taxonomy )
```

## Automatically Clear Cache on Archive Pages for Specific Custom Post Type

By default, adding a post, page or custom post type, clears the cache for the homepage and associated terms or categories associated with it. To clear cache for a specific page when a specific custom post type is added:

```php
add_action( 'save_post', 'custom_clearcache_archive_page' );
/**
 * Clear cache on a specific page when a specific custom post type is added or modified.
 *
 * @param int $post_id
 * @return void
 */
function custom_clearcache_archive_page( $post_id ){
	if(get_post_type() === 'book') {
		pantheon_clear_edge_paths(['/books-on-startups-entrepreneurship-and-venture-capital/']);
	}

	if(get_post_type() === 'public-media') {
		pantheon_clear_edge_paths(['/archives/media/']);
	}
}
```

## More Resources

- [Testing Global CDN Caching](/guides/global-cdn/test-global-cdn-caching)
- [Global CDN Caching for High Performance](/guides/global-cdn/global-cdn-caching)
- [Object Cache (formerly Redis) for Drupal or WordPress](/guides/object-cache)

