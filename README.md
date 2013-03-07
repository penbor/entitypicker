entitypicker
============

A jQuery plugin which utilizes UI autocomplete to allow for more advanced entity (people or users, places, things) picking and editing. It supports all the sources jQuery autocomplete supports, generates HTML input tags that are suitable for submitting through a form as well as the ability to retrieve the chosen entities as JSON objects for use in AJAX style services. Using the entitypicker methods, you can add entities programmatically in order to restore values that have previously been saved (for use on an edit screen, for instance).

Here's a [live demo](http://htmlpreview.github.com/?https://github.com/ErikNoren/entitypicker/blob/master/entitypickerdemo.html?v=6) to check out some of the features.

**New in 0.2.4**
* Added support for maxEntitiesMessage and data-max-entities-message setting. This replaces the static message that was used when the maxEntities was >= 0. This can be a simple string that will always be set or a function (which takes the maxEntities count as a parameter) and, if the resulting string length is > 0 it will be set, otherwise no title is configured.

**New in 0.2.3**
* Added entityValue function to allow a picker to be configured to generate custom input value (see demo)
* Refactored the addEntity and addEntities code. entityadded events are now fired in all cases for each entity. Duplicates are now prevented in addEnities call.
* Refactored the jQuery event bindings a bit to reduce space. Source file is now 600bytes smaller.

**New in 0.2.2**
* Moved the highlight effect (webkit browsers) from dynamic style to dynamic css class for flexibility.
* Added a pre-delete style. This should reduce accidental deletes of entities when using backspace key.

I will try to get more formal documentation up soon but here's some bullet points:
* Uses jQuery UI autocomplete for suggestions and user interaction.
* Entity containers are decorated with jQuery UI classes to give consistent UI.
* Multiple pickers can exists on a page.
* Pickers can be configured with the same or different lookup behaviors.
* The `source` configuration is used directly by jQuery autocomplete. Whatever parameters it supports, entity picker supports.
* Picking an entity generates a container HTML block with a hidden input element.
* The hidden input element's `name` attribute will be set by either the entitypicker element's id or the HTML5 style data attribute `data-input-name`.
* When used in a form the inputs are submitted just like any other group of inputs that share a name attribute.
* Can add single or a group of entities through a JavaScript call. This allows items to be prepopulated on page load (for example on an edit page).
* Has 2 events which fire when an entity is added or removed (entityadded, entityremoved).
* Can take a `maxUsers` parameter during configuration to set max entities that can be picked on each matched elements.
* Can read an HTML5 style data attribute data-max-users on the entitypicker element to set max entities that can be picked.
* Prevents duplicate entity picking by checking the value of the entity being added.
* The minimum number of characters to type before searching can be set on the entitypicker element using the HTML5 style data attribute `data-min-search-length`.
* The default behavior of the autocomplete box to change the value as the user navigates options is disabled. This was confusing for complex search types. A future release could expose this as a configuration option.

The current HMTL5 style data attributes which can be set on individual entitypicker elements (to which you attach the entitypicker) are:
* data-max-entities - sets the maximum number of entities a single picker can hold (default: -1 unlimited)
* data-min-search-length - sets the number of characters to type before a search begins (default: 2)
* data-input-name - sets the name attribute on the hidden input generated by picking an entity (if this isn't present, the id of the entitypicker element is used instead)

To use the picker you need to at least specify the `source` object for the autocomplete control. This is documented on the http://www.jQueryUI.com site.
