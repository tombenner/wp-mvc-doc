---
title: set_object
---
In an action where an `id` URL parameter is available (e.g. the conventional `show` action, where the `id` parameter is passed from the URL), calling `$this->set_object()` will find the object that has the specified id from the controller's native model and make it available to the view as `$object` (using the equivalent of `$this->set('object', $object)`).

{% highlight php %}
<?php
// controllers/venues_controller.php
class VenuesController extends MvcPublicController {
  
  public function show() {
    $this->set_object();
  }
  
}
?>

<?php
// views/venues/show.php
?>
<h2><?php echo $object->name; ?></h2>
{% endhighlight %}