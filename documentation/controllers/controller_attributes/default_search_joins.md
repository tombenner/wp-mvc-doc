---
title: default_search_joins
---
This can be set to make searches in the administrative interface or in the default public search include the specified associations as joins.  This is helpful if you'd like to include fields from associations in `default_searchable_fields`.

{% highlight php %}
<?php
// Event belongs_to Venue and has_and_belongs_to_many Speakers

class Event extends MvcModel {

  var $belongs_to = array('Venue');
  var $has_and_belongs_to_many = array(
    'Speaker' => array(
      'join_table' => '{prefix}events_speakers',
      'fields' => array('id', 'first_name', 'last_name')
    )
  );

}

// We can then set $default_search_joins and $default_searchable_fields to include Speaker and Venue

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

}
?>
{% endhighlight %}