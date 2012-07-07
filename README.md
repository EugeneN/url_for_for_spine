url_for_for_spine
=================

Helper for extending Spne.js Controllers functionality. 
Adds support for generating dynamic urls by name of controller and action. Just like in Pylons.


Usage
=================

1. Put url_for_extender.coffee file to your lib folder in spine app.
2. Import it somewhere (require('lib/url_for_extender')
3. Add some actions to controller by calling add_actions in controllers constructor.

```CoffeeScript

class MyController extends Spine.Controller

  constructor: ->
    super
    @add_actions(
      "/index":"index",
      "/object/edit/:id" : "edit"
    )

    
  index: (args) =>
    # Some logic processing.


  edit: (args) =>
    id = args.id
```

# How to get url?

After importign url_for_extender you have helper object in Spine.
So, when you need to get some url just use Spine.h.url_for("ControllerName", "action", parameters...)
and you will get url.

# using url_for in eco templates.
Also is true for templates.

<%- h = require('lib/url_for_extender') %>

<a href="#<%= h.url_for("MyController", "edit", 7) %>">edit</a>


this will render the folowing:

<a href="#object/edit/7">edit</a>