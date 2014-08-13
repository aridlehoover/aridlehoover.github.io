---
layout: post
title:  Applying the Single Responsibility Principle
date:   2009-02-25 12:56
tags:   OOP
---
I reviewed a bit of code today that presents an excellent opportunity to discuss a big difference between procedural and object-oriented code. Here’s the code I reviewed:

<script src="https://gist.github.com/aridlehoover/637eed9abf6272658a0e.js"></script>

This is a good example of procedural code, where a single method has multiple responsibilities. In this case, the method DisplayCoBrandedImages is:

* Determining if the page should be co-branded;
* Determining if the page is a group page;
* Determining which image to display; and,
* Setting the properties of the image control.

In object-oriented programming, however, we strive to follow the Single Responsibility Principle, which states that code should only have one reason to change. But, any of the tasks mentioned above might change independently of the other tasks. So, if I were to refactor this code into a more object-oriented structure, I would expect to see a different method (or property) handling each of those items above, like this:

<script src="https://gist.github.com/aridlehoover/13538c67d22397249c7c.js"></script>

Now, the primary method (DisplayCoBrandedImages) is only responsible for setting the attributes of the image control. It relies on helper methods (or, as in this case, properties) to perform the other, subordinate tasks. The resulting code, while longer, is easier to understand, because each method is only doing one thing.
