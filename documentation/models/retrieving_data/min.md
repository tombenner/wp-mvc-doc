---
title: min
---
Returns the minimum value of the column (using a `MIN()` MySQL query).  An optional second argument can be used to specify conditions or other query qualifiers.

{% highlight php %}
<?php
// If the Venue table has columns 'event_count' and 'is_public':
$venue_model = mvc_model('Venue');
$min_event_count = $venue_model->min('event_count');
$public_min_event_count = $venue_model->min('event_count', array(
  'conditions' => array(
    'is_public' => 1
  )
));
?>
{% endhighlight %}