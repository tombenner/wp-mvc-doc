---
title: mvc_public_url
---
This returns a URL the corresponds to the routing options that are passed to it.  For example:
{% highlight php %}
<?php
// http://mysite.com/venues/
echo mvc_public_url(array('controller' => 'venues'));

// http://mysite.com/venues/1
echo mvc_public_url(array('controller' => 'venues', 'id' => 1));

// http://mysite.com/venues/my_action/1
echo mvc_public_url(array('controller' => 'venues', 'action' => 'my_action', 'id' => 1));

?>
{% endhighlight %}

Ideally, for `'show'` actions, you would pass an object, as this allows {% doc_link routing/pretty_urls %} to be used if {% doc_link models/model_methods/to_url `to_url()` %} is defined in the model:
{% highlight php %}
<?php
// http://mysite.com/documentation/5/creating-database-tables/
$documentation_node_model = new DocumentationNode();
$documentation_node = $documentation_node_model->find_by_id(5);
echo mvc_public_url(array('object' => $documentation_node));
?>
{% endhighlight %}

Note: If you are looking to make a link to a MVC page from within an MVC page, you may want to use {% doc_link helpers/core_helpers/html the HTML helper's `link()` method %}:
{% highlight php %}
<?php
$this->html->link('All Venues', array('controller' => 'venues'))
?>
{% endhighlight %}