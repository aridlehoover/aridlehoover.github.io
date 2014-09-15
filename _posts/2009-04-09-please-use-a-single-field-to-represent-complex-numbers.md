---
layout: post
title:  Please! Use a single field to represent complex numbers
date:   2009-04-09 18:40
tags:   productivity
---
When creating data entry applications, it is often tempting to represent complex numbers dsuch as Social Security numbers and telephone numbers – as multiple text boxes, like this:

![Phone number fields](http://i.stack.imgur.com/HZZCm.jpg)

The thought is that this simplifies data entry by allowing the end-user to focus on the numbers, not the formatting. Sounds good. But, I’m here to tell you that I have been down this road. It is paved with good intentions. But, you do not want to end up where it will take you.

For brevity, let’s just cut to my preferred solution:

* Use a single text box to represent the complex number
* Use a RequiredFieldValidator to ensure that users don’t skip the field (if necessary)
* With multiple fields, you’d have to write your own custom validator control.
* Use a RegularExpressionValidator to ensure that the data is in an acceptable format

You could split the regular expression into three shorter regular expressions, I suppose. But, why would you want to edit the working regex you grabbed off the Intertubes? That would require you to understand the thing!

The advantages of this approach are:

* Users can enter raw numbers or formatted text (which helps when the user is trying to copy/paste)
* Users can copy/paste in one shot
* Users don’t have to tab between extra fields
* Users can use Backspace and arrow keys to fix typos (without tabbing/clicking around)
* Programmers don’t have to write code to parse/concatenate the fields
* Programmers don’t have to write custom validator code

Everybody wins! And, just to prove how simple it is, here’s the code for Social Security Numbers and North American telephone numbers:

### Social Security Numbers

<script src="https://gist.github.com/aridlehoover/db0ff107bc0fbf8afdd8.js"></script>

Note: The regular expression above allows formatted SSNs as well as raw numbers. Spaces and hyphens are considered acceptable delimiters, but are not required.

### North American Telephone Numbers

<script src="https://gist.github.com/aridlehoover/5bd0160c3aebb507cb78.js"></script>

Note: The North American Numbering Plan (NANP) specifies that the area code and prefix must not begin with 0 or 1, for obvious reasons. The regular expression above validates this. It also handles complex formats as well as raw numbers. Spaces and hyphens are considered acceptable delimiters, but are not required. The area code may or may not be wrapped in parentheses, and may or may not include a space (but not a hyphen) after the trailing parenthesis.
