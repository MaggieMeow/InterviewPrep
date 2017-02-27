# JQuery Notes

I only used jQuery occasionally for a limited set of functions before from other people’s examples. This is a systematic note made from the Code School jQuery tutorials to consolidate and supplement my working knowledge.

## Basics

### Selection
Document Object Model, a tree of HTML nodes

Javascript interacts with DOM. JQuery is more versatile when it comes to dealing with different browsers.

jQuery selector
$(“h1”).text(“something”); // replaces existing text in h1

Make sure DOM is loaded before firing the script. Otherwise, it may not work. So:
$(document).ready(function() {
	$(“h1”).text(“something”);
});

direct child selector >
li:first selects the first element, same for last, even, odd.

$(‘element’).length; // gives number of that element

+$(‘something’).attribute(‘something’) // + makes the string a number

### Traversing
$(“li”).first().next().prev().parent(); // method chaining
$(“li”).find();
$(“#destinations”).children(“li”); // return all direct children
.closest(‘.class’); // return the ancestor found of .class
.parents(‘.class’); // return all parents

### Modifying DOM

$(document).ready(function() {
	var price = $(“<p>something</p>”);
	$(‘.class’).before(price); // adds the price node before .class
	$(‘.class’).before(price); // adds the price node after .class
	$(‘.class’).prepend(price); // adds the price node as the first child of .class
	$(‘.class’).append(price); // adds the price node as the last child of .class
	$(‘.button’).remove(); // removes button from DOM
 	
// an alternative way to add
price.appendTo($(‘.class’));
price.prependTo(…);
… .insertAfter(…);
… .insertBefore(…);

});

$(‘.vacation’).filter(‘something’).addClass(‘highlighted’); // .removeClass() and .toggleClass() is also available
there is also hasClass() boolean

use ‘+varName+' to insert a variable into a string

.slideDown()
.slideUp()
.slideToggle()

### Interaction

.on(<event>, element, <event handler>); // event delegation

e.g. 
$('button').on('click', function() {
  var message = $('<span>Call 1-555-jquery-air to book this tour</span>');
  $(this).append(message); 
  $(this).remove(); // this means only the button clicked instead of all buttons
});

### Listening to events

Don’t put parentheses after a function called in event handler (like use showMessage instead of showMessage()) so that the function is not called immediately.


#### Mouse events
click 
focusing 
mousedown 
mousemove 
mouseover 
mouseenter // when mouse is positioned over the element 
dblclick 
focus out 
mouseup 
mouseout 
mouseleave 

Though they operate the same way, however, the **mouseenter** event only triggers when the mouse pointer enters the selected element. The **mouseover** event is triggered if a mouse pointer enters any child elements as well.

#### Keyboard events
keypress
keydown
keyup // triggered when user stops typing

#### Form Events
blur
select
change
focus
submit

#### Fading
fadeIn()
fadeOut()
fadeToggle()

event.stopPropagation() // when an event happens, it does not bubble up to the ancestors, but does not prevent default behaviour of browser

event.preventDefault(); // prevents default behaviours of browser (like popping to the top of page)

### CSS

.css(‘border-color’, ‘red’);
.css({‘border-color’: ‘red’, 
	‘background-color’: ‘someColor’});
.show() to reverse display: none
 
Preferably, use addClass/toggleClass to keep the styling in the style sheet.

### Animation

.animate(<object>)

e.g. $(this).animate({‘top’: ‘-10px’}, ‘fast’); // fast is 200ms, slow is 600 ms. Can also input number like 400.

OR do this in CSS by adding transition: top 0.2s. But not all browsers support css transitions









