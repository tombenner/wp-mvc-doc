---
title: before
---
To always execute one or more methods before executing the action of the controller, set them in `$before`.

For example, here's how to always run `set_venues()` before every action in EventsController:

{% highlight php %}
<?php
class EventsController extends MvcPublicController {

  var $before = array('set_venues');
  
  public function set_venues() {
    $this->load_model('Venue');
    $venues = $this->Venue->find();
    $this->set('venues', $venues);
  }
  
}
?>
{% endhighlight %}