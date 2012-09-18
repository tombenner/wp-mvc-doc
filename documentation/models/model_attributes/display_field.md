---
title: display_field
---
The name of the field which will be used to textually represent an object in various functions that assume that such a field is available.

{% highlight php %}
<?php
// models/venue.php:

class Venue extends MvcModel {

  var $display_field = 'name';

}

// views/venues/show.php:

// The following will output an anchor tag that uses $object->name for its text.
echo $this->html->venue_link($object);
?>
{% endhighlight %}

The `display_field` value will always be available in the `__name` property of an object (`$object->__name`), allowing you to represent an object textually without knowing exactly what property should be used.

### Using values other than column values for `display_field` 

Note that fields that are set in `after_find()` can also be used for `display_field`, in case the displayed value should be something other than the value of a specific column.

{% highlight php %}
<?php

class Event extends MvcModel {
  
  // The events table doesn't have a column named name, but we'll
  // set $object->name in after_find() below
  var $display_field = 'name';

  public function after_find($object) {
    if (isset($object->speakers)) {
      $speaker_names = array();
      foreach($object->speakers as $speaker) {
        $speaker_names[] = $speaker->name;
      }
      $object->speaker_names = implode(', ', $speaker_names);
      $object->name = $object->speaker_names;
      if (isset($object->venue)) {
        $object->name .= ' at '.$object->venue->name;
      }
    }
  }
  
}

?>
{% endhighlight %}