---
Setting `$wp_post = true;` will automatically create and update a post for each venue; the posts will have a `post_type` value of '`mvc_venue`', but there won't be a [Custom Post Type](http://codex.wordpress.org/Post_Types#Custom_Types) for venues.

{% highlight php %}
<?php
class Venue extends MvcModel {

  var $wp_post = true;

}
?>
{% endhighlight %}

The post of each venue can then be accessed using `$venue->post`, and this will have all of the columns of `wp_posts` as attributes (e.g. `$venue->post->post_title` returns the post's title).