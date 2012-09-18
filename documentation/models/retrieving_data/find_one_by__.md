---
title: find_one_by_*
---
For every attribute of a model, WP MVC will provide a find_one_by_* method that returns the first record with that value for that column.

For example, if Event has a column `venue_id`:

{% highlight php %}
<?php
$event_model = mvc_model('Event');
$event = $event_model->find_one_by_venue_id(4);
?>
{% endhighlight %}