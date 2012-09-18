---
We'll use the code generation utility `wpmvc` to create the initial code of the plugin.  You'll need to have access to the command line to do the following.

Go into the WP MVC directory and make sure that `wpmvc` is executable.

`cd path/to/plugins/wp-mvc`
  
`chmod +x wpmvc`

Generate the plugin's initial code.

`./wpmvc generate plugin VenueListing`

This will generate files in `path/to/plugins/venue-listing/` that create a WP MVC-based plugin.  The plugin can now be activated in WordPress, but before activating it, we'll want to add code for creating a database table during its activation.