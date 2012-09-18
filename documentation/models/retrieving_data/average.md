---
title: average
---
Returns the average of the values of a column (using a `AVERAGE()` MySQL query).  An optional second argument can be used to specify conditions or other query qualifiers.

{% highlight php %}
<?php
// If the Venue table has columns 'event_count' and 'is_public':
$venue_model = mvc_model('Venue');
$event_count_average = $venue_model->average('event_count');
$public_event_count_average = $venue_model->average('event_count', array(
  'conditions' => array(
    'is_public' => 1
  )
));
?>
{% endhighlight %}