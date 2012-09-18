---
title: max
---
Returns the maximum value of the column (using a `MAX()` MySQL query).  An optional second argument can be used to specify conditions or other query qualifiers.

{% highlight php %}
<?php
// If the Venue table has columns 'event_count' and 'is_public':
$venue_model = mvc_model('Venue');
$max_event_count = $venue_model->max('event_count');
$public_max_event_count = $venue_model->max('event_count', array(
  'conditions' => array(
    'is_public' => 1
  )
));
?>
{% endhighlight %}