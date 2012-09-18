---
title: default_searchable_fields
---
This can be set to determine what fields are used in searches within the administrative interface (in an admin controller) or in the default search functionality of a public controller.

{% highlight php %}
<?php
class AdminVenuesController extends MvcAdminController {

  var $default_columns = array(
    'id',
    'name',
    'url' => 'URL'
  );
  var $default_searchable_fields = array('name', 'url');

}
?>
{% endhighlight %}


### Including fields from associated models

To search fields from associated models, you'll need to set list those models in `default_search_joins`.

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