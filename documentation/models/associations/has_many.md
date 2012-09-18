---
To define one or more has many associations, set the `has_many` property.

{% highlight php %}
<?php
class Venue extends MvcModel {

  var $has_many = array('Event');

}
?>
{% endhighlight %}