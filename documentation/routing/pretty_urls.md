---
title: Pretty URLs
---
If you'd like to use pretty URLs for a model, you'll need to do two things:

1. Define `to_url()` in the model and make it return the URL path that should be used when links to the object are created.
1. Set up a corresponding public route

Here's an example:

{% highlight php %}
<?php

// models/documentation_node.php

class DocumentationNode extends MvcModel {
  
  function to_url($object) {
    $slug = $object->title;
    $slug = preg_replace('/[^\w]/', '-', $slug);
    $slug = preg_replace('/[-]+/', '-', $slug);
    $slug = strtolower($slug);
    return 'documentation/'.$object->id.'/'.$slug.'/';
  }
  
}

// config/routes.php

MvcRouter::public_connect('documentation/{:id:[\d]+}.*', array('controller' => 'documentation_nodes', 'action' => 'show'));

?>
{% endhighlight %}
That's it! You will now be able to browse to URLs like `/documentation/65/pretty-urls/`, and whenever you pass an object to one of the methods in the HTML helper (e.g. `$this->html->object_link($object, array('controller' => 'object_nodes'))`) and MvcRouter, the URL that's returned will automatically use the `to_url()` method you defined.