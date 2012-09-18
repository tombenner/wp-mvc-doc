---
WP MVC provides a command line utility for automating the creation (and deletion) of WP MVC-based plugins and the models, views, and controllers used in those plugins.  The utility is located at `plugins/wp-mvc/wpmvc`; before using it, you'll want to make sure that it's executable:

`cd path/to/plugins/wp-mvc`
  
`chmod +x wpmvc`

#### Setting a custom path to the PHP executable

By default, `wpmvc` will use the command `php` to run its code, but you can set a custom path to the PHP executable by setting the environment variable `WPMVC_PHP`.  For example, if you're using MAMP, before running any `wpmvc` commands, you would set `WPMVC_PHP` to the path of MAMP's PHP executable like this:

`export WPMVC_PHP="/Applications/MAMP/bin/php5.3/bin/php"`

#### Setting a custom path to the WordPress directory

If your `wp-content` directory is in a location that's different than the default location (in `ABSPATH.'wp-content'`), you'll need to set the path to WordPress directory, so that the utility knows where to load WordPress from:

`export WPMVC_WORDPRESS_PATH="/srv/www/mysite.com/public_html/wordpress/"`

#### Using the utility on a Windows machine

If you are using a Windows machine, you can run the DOS version of this utility by replacing `./wpmvc` with `wpmvc.bat` in the commands in the following sections.  You'll need to `cd` into the `wp-mvc` directory first, though:

`cd path\to\plugins\wp-mvc`