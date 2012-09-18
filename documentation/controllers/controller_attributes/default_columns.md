---
title: default_columns
---
This defines what columns are shown in an admin controller's default index view.  (A generic index view is provided by WP MVC's core, but it can be overwritten by creating an index.php view in `views/admin/[models]`, where [models] is the tableized model name (e.g. `venues`)).

Each value can be one of the following:

1.   String (without an associative key): Table cell values are found by calling this property on the object. The table header is the string, titleized. 
1.   String (with an associative key): The key is used for the property, and the value is used for the table header.
1.   Array (with an associative key): The key is used for the property.  A `label` key in the array can be used to set the table header, and a `value_method` key can be used to signify that the returned value of the specified method will be used for the table cell.

{% highlight php %}
<?php
class AdminEventsController extends MvcAdminController {
  
  var $default_search_joins = array('Speaker', 'Venue');
  var $default_searchable_fields = array('Speaker.first_name', 'Speaker.last_name', 'Venue.name');
  var $default_columns = array(
    'id',
    'date' => array('value_method' => 'admin_column_date'),
    'time' => array('value_method' => 'admin_column_time'),
    'venue' => array('value_method' => 'venue_edit_link'),
    'speaker_names' => 'Speakers'
  );
  
  public function admin_column_date($object) {
    return empty($object->date) ? null : date('F jS, Y', strtotime($object->date));
  }
  
  public function admin_column_time($object) {
    return empty($object->time) ? null : date('g:ia', strtotime($object->time));
  }
  
  public function venue_edit_link($object) {
    return empty($object->venue) ? null : HtmlHelper::admin_object_link($object->venue, array('action' => 'edit'));
  }
  
}
?>
{% endhighlight %}