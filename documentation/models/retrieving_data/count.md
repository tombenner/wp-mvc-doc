---
title: count
---
Returns the number of records matching the query (using a `COUNT()` MySQL query).

{% highlight php %}
<?php
$venue_model = mvc_model('Venue');
$total_count = $venue_model->count();
$public_count = $venue_model->count(array(
  'conditions' => array(
    'is_public' => 1
  )
));
?>
{% endhighlight %}