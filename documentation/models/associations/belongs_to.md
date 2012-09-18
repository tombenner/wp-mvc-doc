---
To define one or more belongs to associations, set the `belongs_to` property.

{% highlight php %}
<?php
class Event extends MvcModel {

  var $belongs_to = array('Venue');

}
?>
{% endhighlight %}

In this example, the events table should have a `venue_id` column, which will be used as the foreign key.

After this association has been defined, you can now easily include associated data in finds {add more}.

A custom foreign key can also be defined:

{% highlight php %}
<?php
class Event extends MvcModel {

  var $belongs_to = array(
    'Venue' => array(
      'foreign_key' => 'my_venue_id'
    )
  );

}
?>
{% endhighlight %}