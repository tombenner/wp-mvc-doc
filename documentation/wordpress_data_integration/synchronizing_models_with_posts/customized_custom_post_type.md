---
Setting `'post_type'` to an array lets you customize the custom type and how it behaves.  Accepted properties are:

* `'args'` - Same as the `$args` settings in [register_post_type](http://codex.wordpress.org/Function_Reference/register_post_type)
* `'fields'` - How the fields of the post should be set whenever the object is updated (see below)

#### Types of values for `'fields'`
* `'generate_post_title()'` would use the value returned by `generate_post_title($object)` in the model
* `'$description'` would use the value of $object->description (i.e. the `description` column in the table)
* `'draft'` would always use the string `'draft'`

{% highlight php %}
<?php
class Venue extends MvcModel {

  var $wp_post = array(
    'post_type' => array(
      'args' => array(
        'show_in_menu' => true,
        'supports' => array('title')
      ),
      'fields' => array(
        'post_title' => 'generate_post_title()',
        'post_content' => '$description',
        'post_status' => 'draft'
      )
    )
  );
  
  function generate_post_title($object) {
    return 'The '.$object->name;
  }

}
?>
{% endhighlight %}