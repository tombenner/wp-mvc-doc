---
Go back to the command line, and in the `plugins/wp-mvc` directory, generate scaffolding (initial code for a resource's model, views, and controllers) for the Venue resource:

`./wpmvc generate scaffold VenueListing Venue`

This will create a model, views, a public controller, and an admin controller for venues in `plugins/venue-listing/app/`.  You will also now see an admin menu for managing venues.

#### Modify the admin views

The generated code only uses the `name` column, so let's add fields to the `add` and `edit` forms for the other columns.

{% highlight php %}
<?php
// app/views/admin/venues/add.php
?>

<h2>Add Venue</h2>

<?php echo $this->form->create($model->name); ?>
<?php echo $this->form->input('name'); ?>
<?php echo $this->form->input('url', array('label' => 'URL', 'style' => 'width: 300px;')); ?>
<?php echo $this->form->input('address1', array('label' => 'Address 1')); ?>
<?php echo $this->form->input('address2', array('label' => 'Address 2')); ?>
<?php echo $this->form->input('city'); ?>
<?php echo $this->form->input('state', array('style' => 'width: 40px;')); ?>
<?php echo $this->form->input('zip', array('style' => 'width: 80px;')); ?>
<?php echo $this->form->input('description'); ?>
<?php echo $this->form->end('Add'); ?>
{% endhighlight %}

{% highlight php %}
<?php
// app/views/admin/venues/edit.php
?>

<h2>Edit Venue</h2>

<?php echo $this->html->object_link($object, array('controller' => 'venues', 'text' => 'View')); ?>

<?php echo $this->form->create($model->name); ?>
<?php echo $this->form->input('name'); ?>
<?php echo $this->form->input('url', array('label' => 'URL', 'style' => 'width: 300px;')); ?>
<?php echo $this->form->input('address1', array('label' => 'Address 1')); ?>
<?php echo $this->form->input('address2', array('label' => 'Address 2')); ?>
<?php echo $this->form->input('city'); ?>
<?php echo $this->form->input('state', array('style' => 'width: 40px;')); ?>
<?php echo $this->form->input('zip', array('style' => 'width: 80px;')); ?>
<?php echo $this->form->input('description'); ?>
<?php echo $this->form->end('Update'); ?>
{% endhighlight %}

#### Modify the public views

Let's display the venue address and a link to its website in the public `show` view.

{% highlight php %}
<?php
// app/views/venues/show.php
?>

<h2><?php echo $object->name; ?></h2>

<div>
  <?php echo $this->html->link('Website', $object->url); ?>
</div>

<?php
  echo '<div>'.$object->address1.'</div>';
  if (!empty($object->address2)) {
    echo '<div>'.$object->address2.'</div>';
  }
  echo '<div>'.$object->city.', '.$object->state.', '.$object->zip.'</div>';
?>

<p>
  <?php echo $this->html->link('All Venues', array('controller' => 'venues')); ?>
</p>
{% endhighlight %}

That's it!  You can now begin to add venues in the admin section in Venues > Add New, edit them, view them at public-facing URLs like /venue/1/, and see a paginated list of them at /venues/.