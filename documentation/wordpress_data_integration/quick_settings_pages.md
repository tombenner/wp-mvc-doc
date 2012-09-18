---
To both [register settings](http://codex.wordpress.org/Function_Reference/register_setting) for your MVC plugin and create a page in the "Settings" admin menu where users can adjust those settings, you can simply define a class that extends MvcSettings in `app/settings/`.

The `'type'` attribute can be `'text'`, `'textarea'`, `'checkbox'`, or `'select'` (for which you should provide `'options'` or `'options_method'`).

{% highlight php %}
<?php
// app/settings/documentation_settings.php
class DocumentationSettings extends MvcSettings {

  var $settings = array(
    'admin_version_id' => array(
      'type' => 'select',
      'label' => 'Admin Version',
      'options_method' => 'get_all_versions',
      'default' => 1
    ),
    'public_version_id' => array(
      'type' => 'select',
      'label' => 'Public Version',
      'options_method' => 'get_all_versions',
      'default' => 1
    ),
    'show_search_form' => array(
      'type' => 'checkbox',
      'default' => 1
    ),
    'show_version_list' => array(
      'type' => 'checkbox',
      'default' => 0
    )
  );
  
  public function get_all_versions() {
    $documentation_version_model = mvc_model('DocumentationVersion');
    $versions = $documentation_version_model->find();
    $list = array();
    foreach ($versions as $version) {
      $list[$version->id] = $version->name;
    }
    return $list;
  }
  
}
?>
{% endhighlight %}


To retrieve the value of the `'admin_version_id'` setting below, you would use `mvc_setting()` like this:

{% highlight php %}
<?php
$admin_version_id = mvc_setting('DocumentationSettings', 'admin_version_id');
?>
{% endhighlight %}