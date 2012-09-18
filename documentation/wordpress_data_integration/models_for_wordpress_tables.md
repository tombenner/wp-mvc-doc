---
The following models, which each use the corresponding WordPress table, are defined by WP MVC:

* MvcComment
* MvcCommentMeta
* MvcPost
* MvcPostMeta
* MvcUser
* MvcUserMeta

You can thus make associations between your app's models and WordPress tables.  For example, you could define an Organization model that has_many members who are WordPress users (i.e. records in the wp_users table):

{% highlight php %}
<?php
class Organization extends MvcModel {

  var $has_many = array(
    'Member' => array(
      'class' => 'MvcUser'
    )
  );
  
}
?>
{% endhighlight %}

Then, in the controller, you could get the list of members for an organization with `$organization->members`:

{% highlight php %}
<?php
class OrganizationsController extends MvcPublicController {

  public function show() {
    $organization = $this->model->find_by_id($this->params['id']);

    if (!empty($organization)) {
      $this->set('organization', $organization);
      $this->set('members', $organization->members);
    } 
  }


}
?>
{% endhighlight %}