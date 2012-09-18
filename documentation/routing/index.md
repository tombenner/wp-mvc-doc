---
By default, WP MVC sets up the following public routes:

{% highlight php %}
<?php
MvcRouter::public_connect('{:controller}', array('action' => 'index'));
MvcRouter::public_connect('{:controller}/{:id:[\d]+}', array('action' => 'show'));
MvcRouter::public_connect('{:controller}/{:action}/{:id:[\d]+}');
?>
{% endhighlight %}

The first line makes URLs like `/venues/` use `array('controller' => 'venues', 'action' => 'index')`.

The second line makes URLs like `/venues/23` use `array('controller' => 'venues', 'action' => 'show', 'id' => 23)`.

The third line makes URLs like `/venues/custom_action/23` use `array('controller' => 'venues', 'action' => 'custom_action', 'id' => 23)`.

Routing of admin pages is handled more behind the scenes, but you can adjust what admin pages are available by setting a model's `admin_pages` attribute.

To set up an [admin AJAX call](http://codex.wordpress.org/AJAX_in_Plugins#Ajax_on_the_Administration_Side), use `MvcRouter::admin_ajax_connect()`.

### Custom routing

To set up your own public routing and/or admin AJAX routing, add a file at `app/config/routes.php` containing code like the following:

{% highlight php %}
<?php

// app/config/routes.php

MvcRouter::public_connect('', array('controller' => 'documentation_nodes', 'action' => 'index'));
MvcRouter::public_connect('documentation/{:id:[\d]+}.*', array('controller' => 'documentation_nodes', 'action' => 'show'));
MvcRouter::public_connect('search', array('controller' => 'documentation_nodes', 'action' => 'search'));
MvcRouter::public_connect('{:controller}', array('action' => 'index'));
MvcRouter::public_connect('{:controller}/{:id:[\d]+}', array('action' => 'show'));
MvcRouter::public_connect('{:controller}/{:action}/{:id:[\d]+}');

MvcRouter::admin_ajax_connect(array('controller' => 'admin_documentation_nodes', 'action' => 'update_tree'));
MvcRouter::admin_ajax_connect(array('controller' => 'admin_documentation_nodes', 'action' => 'preview_content'));

?>
{% endhighlight %}

The second `admin_ajax_connect()` call above allows for an AJAX call like the following to be made:

{% highlight js %}
jQuery(document).ready(function(){
  
  // Data to send to the AJAX call
  var data = {
    action: 'admin_documentation_nodes_preview_content',
    content: 'my_content'
  };
  
  // ajaxurl is defined by WordPress
  jQuery.post(ajaxurl, data, function(response){
    // Handle the response
  });
  
});
{% endhighlight %}