---
As in any other WordPress plugin, database tables used in WP MVC-based plugins should be created during the plugin's activation using WordPress's [dbDelta()](http://codex.wordpress.org/Creating_Tables_with_Plugins#Creating_or_Updating_the_Table) function (which allows for modifications of the table to be made by later versions of the plugin).

The plugin loader class that is automatically created by the `./wpmvc generate plugin MyPlugin` command ({% doc_link creating_plugins read more %}) provides all of the necessary code for this, except for the SQL code, which you'll need to write.

For example, to create a table named `venues` in a plugin named MyPlugin, you would want add the SQL to the activate() method in `plugins/my-plugin/my_plugin_loader.php` like this:

{% highlight php %}
<?php
function activate() {

// The $this->activate_app(__FILE__) call needs to be made to
// activate this app within WP MVC

$this->activate_app(__FILE__);

require_once ABSPATH.'wp-admin/includes/upgrade.php';

add_option('my_plugin_db_version', $this->db_version);

$sql = '
  CREATE TABLE '.$this->tables['venues'].' (
    id int(11) NOT NULL auto_increment,
    name varchar(255) NOT NULL,
    sort_name varchar(255) NOT NULL,
    url varchar(255) default NULL,
    description text,
    address1 varchar(255) default NULL,
    address2 varchar(255) default NULL,
    city varchar(100) default NULL,
    state varchar(100) default NULL,
    zip varchar(20) default NULL,
    PRIMARY KEY  (id)
  )';
dbDelta($sql);

}
?>
{% endhighlight %}