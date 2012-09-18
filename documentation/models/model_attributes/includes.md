---
title: includes
---
To include associated models by default in SELECT queries, set `$includes` to an array of model names for which associations have already been defined.  For example:

{% highlight php %}
<?php
class Event extends MvcModel {

  var $belongs_to = array('Venue');
  var $has_and_belongs_to_many = array(
    'Speaker' => array(
      'join_table' => '{prefix}events_speakers',
      'fields' => array('id', 'first_name', 'last_name')
    )
  );
  var $includes = array('Venue', 'Speaker');

}
?>
{% endhighlight %}