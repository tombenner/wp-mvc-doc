---
title: mvc_render_to_string
---
This lets you capture the output of a view as a string.  The first argument is the view path, and the second is an array of variables that the view will use (this is optional).

{% highlight php %}
<?php
// Somewhere in the theme:
?>
<?php
$venue_model = mvc_model('Venue');
$venues = $venue_model->find(array('limit' => 5));
$venues_list_html = mvc_render_to_string('venues/list', array('objects' => $venues));
?>
<ul class="venues-list"><?php echo $venues_list_html; ?></ul>

<?php
// In app/views/venues/list.php:
?>
<?php foreach($objects as $object): ?>
  <li><?php echo $this->html->venue_link($object); ?></li>
<?php endforeach; ?>
{% endhighlight %}