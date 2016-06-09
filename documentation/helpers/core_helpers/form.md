---
The form helper is primarily aimed at creating forms for adding and editing data.  Its workhorse method is `input()`, which checks the field type in the database schema and outputs a form element appropriate to the data type (e.g. a text input for VARCHAR, a textarea for TEXT, etc).

It also provides methods for creating inputs for associations, as shown below.

{% highlight php %}
<?php

// controllers/admin/events_controller.php

class AdminEventsController extends MvcAdminController {

  public function edit() {
    $this->set_speakers();
    $this->set_venues();
    $this->verify_id_param();
    $this->set_object();
    $this->create_or_save();
  }
  
  private function set_speakers() {
    $this->load_model('Speaker');
    $speakers = $this->Speaker->find(array('selects' => array('id', 'first_name', 'last_name')));
    $this->set('speakers', $speakers);
  }
  
  private function set_venues() {
    $this->load_model('Venue');
    $venues = $this->Venue->find(array('selects' => array('id', 'name')));
    $this->set('venues', $venues);
  }
  
}
?>

<?php

// views/admin/events/edit.php

$formatted_time = preg_replace('/:00$/', '', $object->time);

?>

<h2><?php echo MvcInflector::titleize($this->action); ?> <?php echo MvcInflector::titleize($model->name); ?></h2>

<?php echo $this->form->create($model->name); ?>
<?php echo $this->form->belongs_to_dropdown('Venue', $venues, array('style' => 'width: 200px;', 'empty' => true)); ?>
<?php echo $this->form->input('date', array('label' => 'Date (YYYY-MM-DD)')); ?>
<?php echo $this->form->input('time', array('label' => 'Time (24-hour clock)', 'value' => $formatted_time)); ?>
<?php echo $this->form->input('description'); ?>
<?php echo $this->form->has_many_dropdown('Speaker', $speakers, array('style' => 'width: 200px;', 'empty' => true)); ?>
<?php echo $this->form->input('is_public'); ?>
<?php echo $this->form->end('Update'); ?>
{% endhighlight %}

### Methods

#### create($model_name, $options=array())

#### end($label='Submit')

#### input($field_name, $options=array())

#### text_input($field_name, $options=array())

#### textarea_input($field_name, $options=array())

#### checkbox_input($field_name, $options=array())

#### hidden_input($field_name, $options=array())

#### select($field_name, $options=array())

#### select_tag($field_name, $options=array())

#### button($text, $options=array())

#### belongs_to_dropdown($model_name, $select_options, $options=array())

#### has_many_dropdown($model_name, $select_options, $options=array())
