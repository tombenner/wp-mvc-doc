---
title: load_helper
---
To use a helper in a view, you'll need to call `$this->load_helper()` in the controller.

{% highlight php %}
<?php
// controllers/venues_controller.php
class VenuesController extends MvcPublicController {
  
  public function show() {
    $this->load_helper('VenueDisplay');
    $this->set_object();
  }
  
}
?>

<?php
// views/venues/show.php
?>
<h2><?php echo $object->name; ?></h2>
<?php echo $this->venue_display->formatted_address($object); ?>

<?php
// helpers/venue_display_helper.php
class VenueDisplayHelper extends MvcHelper {
  
  public function formatted_address($object) {
    $html = '';
    $html .= '<div>'.$object->address1.'</div>';
    $html .= '<div>'.$object->address2.'</div>';
    $html .= '<div>'.$object->city.', '.$object->state.' '.$object->zip.'</div>';
    return $html;
  }

}
?>
{% endhighlight %}