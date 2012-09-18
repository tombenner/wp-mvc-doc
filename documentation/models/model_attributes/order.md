---
title: order
---
This can be used to set the default order that is used in SELECT queries.  For example:

{% highlight php %}
<?php
class Venue extends MvcModel {

  var $order = 'Venue.name ASC, Venue.id ASC';

}
?>
{% endhighlight %}