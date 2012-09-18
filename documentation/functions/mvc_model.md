---
title: mvc_model
---
This allows you to easily use a {% doc_link models WP MVC model %} from elsewhere in WP (e.g. in a theme).  Pass the name of a model to it, and it will return an instantiation of the model that has all of the standard model methods and attributes.

{% highlight php %}
<?php
$venue_model = mvc_model('Venue');
$venues = $venue_model->find(array('limit' => 5));
?>
{% endhighlight %}