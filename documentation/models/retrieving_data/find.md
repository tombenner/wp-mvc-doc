---
title: find
---
The `find()` method is the all-purpose method for retrieving data from a model.  It takes a single argument, an associative array of options for the find.  Here's an example that shows the available options (it isn't a practical example, though):

{% highlight php %}
<?php
// controllers/events_controller.php
class EventsController extends MvcPublicController {
  
  public function index() {
    $objects = $this->Event->find(array(
      'joins' => array('Venue'),
      'includes' => array('Venue'),
      'selects' => array('Venue.id', 'Venue.name', 'Event.date', 'Event.active'),
      'additional_selects' => array('Event.date'),
      'conditions' => array(
        'Event.active' => 1,
        'Event.date >=' => date('Y-m-d'),
        'Venue.id' => array(56, 83) // Venue.id IN (56, 83)
      ),
      'group' => 'Event.id',
      'order' => 'Event.date DESC',
      'page' => 1
      'per_page' => 20
    ));
    $this->set('objects', $objects);
  }
  
}
?>
{% endhighlight %}

#### joins
An array of associated models that will be included as joins in the query and in the results.

#### includes
An array of associated models that will be added to the object via additional SELECT queries after the initial SELECT query has been made.  These can't be referenced in `conditions`, but unlike `joins`, has_many and has_and_belongs_to many associations can be safely used here.

#### selects
An array of columns that will be selected in the query.  This will replace the default selected fields that are defined in the model.

#### additional_selects
An array of columns that will be merged with the default selected fields that are defined in the model; all of the columns in the resulting merged array will be selected in the query.

#### conditions
An array of conditions for the WHERE part of the query.  Conditions are joined with an AND by default, but OR conditions can be done like this: 

{% highlight php %}
<?php
// Find all Events that are active or are happening on or after today
$objects = $this->Event->find(array(
  'conditions' => array(
    'OR' => array(
      'Event.active' => 1,
      'Event.date >=' => date('Y-m-d'),
    )
  )
);
?>
{% endhighlight %}

To group conditions together, use an `'AND'` or `'OR'` in the same way that the `'OR'` above is used.

#### group
A string specifying the value for a GROUP BY clause.

#### order
A string specifying the value for an ORDER clause.

#### page
An integer specifying which page of results should be returned.  The number of results per page defaults to the `per_page` property of the model, but can be overwritten with a `per_page` key in the find options.

#### per_page
An integer specifying the number of results per page.  This is only relevant when the `page` option is also set.