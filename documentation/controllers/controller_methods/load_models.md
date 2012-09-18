---
title: load_models
---
Use `load_models()` if you want to use models other than the controller's native model.  To load a single model, use {% doc_link controllers/controller_methods/load_model load_model() %}.

{% highlight php %}
<?php
// controllers/venues_controller.php
class VenuesController extends MvcPublicController {
  
  public function show() {
    $this->load_models('Speaker', 'Event');
    $speakers = $this->Speaker->find();
    $events = $this->Event->find();
  }
  
}
?>
{% endhighlight %}