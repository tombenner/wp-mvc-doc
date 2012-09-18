---
title: after
---
To always execute one or more methods after executing the action of the controller, set them in `$after`.

For example, here's how to always run `set_venues()` after every action in EventsController:

{% highlight php %}
<?php
class EventsController extends MvcPublicController {

  var $after = array('set_venues');
  
  public function set_venues() {
    $this->load_model('Venue');
    $venues = $this->Venue->find();
    $this->set('venues', $venues);
  }
  
}
?>
{% endhighlight %}