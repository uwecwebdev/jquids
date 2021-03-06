Jquids
======

This is a rewrite of Tim Harper's "Calendar Date Select" gem
(https://github.com/timcharper/calendar_date_select) using the jQuery UI date
picker.  This project is still in development and still far from working.

The projects intent is to simulate the ease of use of the original while:

- Updating the code to work with Rails 3
- Using the hosted jQuery UI infastructure to avoid local dependencies


Jquids stands for JQuery UI Date Select


Usage
-----

Add the following some where in your page (preferablly in the head of your
layout file):

    <%= jquids_includes %>

Change a field to so it uses the `jquids_tag`:

    <%= jquids_tag "some_date" %>

and you should be good to go!


Customization
-------------

CalendarDateSelect allow for the use of many different formats and css styles,
and Jquids was made to allow for that same kind of flexibility, with
out all of the weight of an full library of javascript and css files in your
public folder.


### jQeury Version

To specify a different version of jQuery, just include :jQuery => "X.X.X" to
your 'jquids_includes' method:

    <%= jquids_includes :jQuery => "1.6.0" %>

A list of supported versions numbers can be found at the bottom of the page.

Because it is entirely possible that you are already using jQuery in your
application, the option is given to you to not include jQuery using
Jquids.  To do that, just add :jQuery => :none to your
'jquids_includes' method:

    <%= jquids_includes :jQuery => :none %>

and now jQuery will not be included into your plugin.


### jQuery UI Version

Just like you can specify a specific version of jQuery, you can also specify a
version of jQuery UI that you would prefer to use:

    <%= jquids_includes :jQueryUI => "1.8.0" %>

A list of supported version numbers can be found at the bottom of the page.

You are also able tell the Jquids not to load jQuery UI in the same way
that you did with jQuery:

    <%= jquids_includes :jQueryUI => :none %>

You may also use `nil` or `false`.


### Custom Style

To change the style, just add `:style => :new_style` to the
`jquids_includes` declaration:

    <%= jquids_includes :style => :vader %>

And the new style will be applied.  All styles come from the Google CDN
(http://code.google.com/apis/libraries/devguide.html), so they are not hosted
in your application.  If you wish to theme roll your own style
(http://jqueryui.com/themeroller/), just set `:style` to `:none`, `nil`, or
`false`, and include your style sheet in your project.

All styles that are available via the Google CDN for jQueryUI can be found
below.


### Custom Format

To set the format the same way that was done with CalendarDateSelect, just set
the Jquids format variable using the `format=` function somewhere in
your code:

    <% Jquids.format= :american %>

or you can set it in `jquids_includes` method by setting the
`:format` variable in the options hash:

    <%= jquids_includes :format => :american %>

All the formats used mimic what was used in the original CalendarDateSelect
gem.  The formats available are listed below.


### Customizing the jQuery UI Datepicker

The jQuery datepicker has many options that you can implement through
Jquids via the `:datepicker_options` hash.  To add an option to a
single datepicker element, simply add the hash as an argument to
`jquids_tag` call:

    <%= jquids_tag "some_date", nil, :datepicker_options => {:showButtonPanel => true} %>

and now the datepicker will use the jQueryUI's button panel at the bottom of
the datepicker for that instance.  But if you have multiple instances that all
should have the `showButtonPanel` equal to true, add the `:datepicker_options`
to the `jquids_includes`:

    <%= jquids_includes :datepicker_options => {:showButtonPanel => true} %>

and the change will be applied to all instances of the datepicker.  You can
overide that change by setting the setting to false on the desired
`jquids_tag` instances.

A full list of all of the jQueryUI functions can be found here:
http://jqueryui.com/demos/datepicker/#options


jQuery Versions
---------------
"1.2.3, 1.2.6, 1.3.0, 1.3.1, 1.3.2, 1.4.0, 1.4.1, 1.4.2, 1.4.3, 1.4.4, 1.5.0,
1.5.1, 1.5.2, 1.6.0, 1.6.1"


jQuery UI Versions
------------------
"1.5.2, 1.5.3, 1.6.0, 1.7.0, 1.7.1, 1.7.2, 1.7.3, 1.8.0, 1.8.1, 1.8.2, 1.8.4,
1.8.5, 1.8.6, 1.8.7, 1.8.8, 1.8.9, 1.8.10, 1.8.11, 1.8.12, 1.8.13"


Styles
------

The default style is `:base`.  The following can be implemented via the
`jquids_includes` function:

* `:base`
* `:black_tie`
* `:blitzer`
* `:cupertino`
* `:dark_hive`
* `:dot_luv`
* `:eggplant`
* `:excite_bike`
* `:flick`
* `:hot_sneaks`
* `:humanity`
* `:le_frog`
* `:mint_choc`
* `:overcast`
* `:pepper_grinder`
* `:redmond`
* `:smoothness`
* `:south_street`
* `:start`
* `:sunny`
* `:swanky_purse`
* `:trontastic`
* `:ui_darkness`
* `:ui_lightness`
* `:vader`


Formats
-------

The default format is `:natural`.  Other formats include:

* `:natural` = "%B %d, %Y"
* `:hyphen_ampm` = "%Y-%m-%d"
* `:iso_date` = "%Y-%m-%d"
* `:finnish` = "%d.%m.%Y"
* `:danish` = "%d/%m/%Y"
* `:american` = "%m/%d/%Y"
* `:euro_24hr` = "%d %B %Y"
* `:euro_24hr_ymd` = "%Y.%m.%d"
* `:italian` = "%d/%m/%Y"
* `:db` = "%Y-%m-%d"

The only two formats currently with time
in am-pm is `:natural`, `:hyphen_ampm`, and `:american`.


TODO
----

- Allow for setting the format via the `jquids_includes` method and
  the ability to set it on a case by case basis (implemented, but has a bug)
- Map the option settings for CalendarDateSelect to Jquids
- Get callbacks working
- Get it to work in rails 2 and 3 (with tests)
- Integrate with formtastic


Contribute/Suggestions
----------------------
Suggestions and contributions to the project are welcome.
