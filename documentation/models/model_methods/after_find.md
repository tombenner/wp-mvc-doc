---
title: after_find
---
To process an object immediately before it is returned from a `find()` or `paginate()` call, define `after_find()`.  This can be useful if you want to always add a commonly-needed property to objects that is something other than the values of the model's table columns.

{% highlight php %}
<?php
class Event extends MvcModel {

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