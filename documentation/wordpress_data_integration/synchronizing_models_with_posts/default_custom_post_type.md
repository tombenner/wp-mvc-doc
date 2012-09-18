---
Setting `$wp_post = array('post_type' => true);` behaves the same as above, but now a [Custom Post Type](http://codex.wordpress.org/Post_Types#Custom_Types) will be created.  By default, this post type is kept fairly private (e.g. it doesn't show up in Navigation Menus), but this can be changed by customizing it (see the next section).

{% highlight php %}
<?php
class Venue extends MvcModel {

  var $wp_post = array('post_type' => true);

}
?>
{% endhighlight %}