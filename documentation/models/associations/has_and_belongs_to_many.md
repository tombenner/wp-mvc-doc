---
To define one or more has and belongs to many associations, set the `has_and_belongs_to_many` property.

WP MVC will attempt a guess at the join table, but you may want to specify it (use `{prefix}` in the table name as a token that will be replaced by `$wpdb->prefix`).  You can also specify what fields are retrieved from the table.

{% highlight php %}
<?php
class Event extends MvcModel {
  var $has_and_belongs_to_many = array(
    'Speaker' => array(
      'join_table' => '{prefix}events_speakers',
      'fields' => array('id', 'first_name', 'last_name')
    )
  );
}
?>
{% endhighlight %}