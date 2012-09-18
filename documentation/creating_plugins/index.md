---
### Overview

WP MVC provides a command line utility for automating the creation (and deletion) of WP MVC-based plugins and the models, views, and controllers used in those plugins.  The utility is located at `plugins/wp-mvc/wpmvc`; before using it, you'll want to make sure that it's executable:

`cd path/to/plugins/wp-mvc`
  
`chmod +x wpmvc`

See {% doc_link creating_plugins/generating_code %} for more information on this utility, including how to use it on a Windows machine, how to set a custom path to the PHP executable (this is necessary in MAMP), and how to set a custom path to the WordPress directory.

### Creating a WP MVC-based plugin

To create a WordPress plugin that will use WP MVC, run the following:

`./wpmvc generate plugin MyPlugin`

This will create the directory `plugins/my-plugin/`, the files necessary for the plugin to be activated, and a skeleton structure of the `app/` directory.  

### Creating models, views, and controllers for a WP MVC-based plugin

After creating a plugin, you'll want to generate code for the models, views, and controllers of each of its resources.  To create all of these for a given resource (e.g. a resource named MyVenue that represents venues), run the following, where `MyPlugin` is the name of your plugin and `MyVenue` is the name of your resource:

`./wpmvc generate scaffold MyPlugin MyVenue`

The generated code will be in `plugins/my-plugin/app/` and assumes that a database column named `name` is present and will be used to represent the resource in views, but this can easily be modified. There will now be an administrative menu (`My Venues`) for this resource in WordPress, and you'll be able to browse to URLs like /my_venues/ and /my_venues/1/ to see the public-facing views.

### Other commands

The `wpmvc` utility can also be used to selectively create or delete the model, views, or controllers for a specified resource.  Here are some examples that should be fairly self-explanatory:

`./wpmvc generate model MyPlugin MyVenue`

`./wpmvc generate views MyPlugin MyVenue`

`./wpmvc generate controllers MyPlugin MyVenue`

`./wpmvc destroy model MyPlugin MyVenue`

`./wpmvc destroy views MyPlugin MyVenue`

`./wpmvc destroy controllers MyPlugin MyVenue`