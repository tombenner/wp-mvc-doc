---
title: set
---
Use `set()` to make variables from the controller available in the view.

{% highlight php %}
<?php
// controllers/venues_controller.php
class VenuesController extends MvcPublicController {
  
  public function show() {
    $object = $this->model->find_by_id($this->params['id'], array(
      'includes' => array('Event')
    ));
    $this->set('object', $object);
  }
  
}

<?php
// views/venues/show.php
?>
<h2><?php echo $object->name; ?></h2>
{% endhighlight %}