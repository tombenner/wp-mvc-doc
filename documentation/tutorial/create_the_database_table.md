---
To create a table to store our venues, open up `plugins/venue-listing/venue_listing_loader.php`.  The `activate()` method is called when this plugin is activated, so we'll want to create our table here using WordPress's [dbDelta()](http://codex.wordpress.org/Creating_Tables_with_Plugins#Creating_or_Updating_the_Table) function.  Add a few lines to `activate()` so that it looks like this:

{% highlight php %}
<?php
function activate() {

  // This call needs to be made to activate this app within WP MVC
  
  $this->activate_app(__FILE__);
  
  // Perform any databases modifications related to plugin activation here, if necessary

  require_once ABSPATH.'wp-admin/includes/upgrade.php';

  add_option('venue_listing_db_version', $this->db_version);
  
  // Use dbDelta() to create the tables for the app here
  
  global $wpdb;
  $sql = '
    CREATE TABLE '.$wpdb->prefix.'venues (
      id int(11) NOT NULL auto_increment,
      name varchar(255) NOT NULL,
      url varchar(255) default NULL,
      description text,
      address1 varchar(255) default NULL,
      address2 varchar(255) default NULL,
      city varchar(100) default NULL,
      state varchar(5) default NULL,
      zip varchar(20) default NULL,
      PRIMARY KEY  (id)
    )';
  dbDelta($sql);
  
}
?>
{% endhighlight %}

Now activate the plugin, and the table will be created.