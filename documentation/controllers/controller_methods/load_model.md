---
title: load_model
---
Use `load_model()` if you want to use a model other than the controller's native model.  To load multiple models, use {% doc_link controllers/controller_methods/load_models load_models() %}.

{% highlight php %}
<?php
// controllers/venues_controller.php
class VenuesController extends MvcPublicController {
  
  public function show() {
    $this->load_model('Speaker');
    $speakers = $this->Speaker->find();
  }
  
}
?>
{% endhighlight %}