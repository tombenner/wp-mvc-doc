---
To define validations for the fields of the model, set the `validate` property.  You can either use predefined rules by setting `rule` (see the example below)  use a custom regular expression by setting `pattern`.

Predefined rules currently include:

* `alphanumeric` - The value must contain only letters and numbers
* `email` - The value must be a valid email address
* `numeric` - The value must be numeric, as defined by PHP's [is_numeric()](http://php.net/is_numeric) function
* `not_empty` - The value must contain characters other than whitespace characters
* `url` - The value must be a valid URL

For example:

{% highlight php %}
<?php
class Speaker extends MvcModel {

  var $validate = array(
    // Use a custom regex for the validation of the first_name field
    'first_name' => array(
      'pattern' => '/^[A-Z]/',
      'message' => 'Please enter a capitalized name in the First Name field!'
    ),
    // Use a predefined rule (which includes a generalized message)
    'last_name' => 'not_empty',
    // Use a predefined rule, but allow the field to be empty ('required' => false) and supply
    // a custom message
    'url' => array(
      'rule' => 'url',
      // A value for this is not required, but if a value is supplied, the rule will need to be
      // passed
      'required' => false,
      // Use a message other than the url rule's default message
      'message' => 'Please enter a valid URL in the URL field!'
    )
  );
  
}
?>
{% endhighlight %}