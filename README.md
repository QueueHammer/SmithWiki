#SmithWiki#

A JavaScript based Wiki. Built using jQuery, Underscore, Backbone, Mustache, and Amplify.

---

In the past I had used javascript wiki called TiddlyWiki. However modern browsers add restrictions to local file modification, disabling any permanent changes to TiddlyWiki.
Looking at the idea of making my own I realised that a number of frameworks had been created to make developing such an app easier.
Specifically jQuery to clean up working with the DOM, Backbone for managing Views / Local Routes, Mustache for templating, and Amplify for persistent storage.

---

##Features##

All pages are local routes
```
wiki.html/#pages/mypage => the wiki page "mypage"
wiki.html/#edit/anotherpage => edits "anotherpage"
```

New Wiki pages are defined by boxing text with pipes. Clicking the link will take you to the page or if it does not exist allows you edit the entry for that page. Saving your changes creates it.
```
This would be raw text in a wiki page and a link to |mypage|.
```

The syntax for editing pages is MarkDown, a popular meta formatting syntax for text used by StackOverflow, GitHub, and others.
```
#This would be an H1#
* With bullet points
* Your standard un-ordered list
* Simple really
* And links to |newpages| are taken care of 
```

The views are Mustache templates. Additionally any text wrapped in triple curly braces will be checked if it exists as a page and its content used to fill in that part of the template. This means the header, menu or any other parts of the Pages view you specify is derived from your own entries in the Wiki.
```html
<div class="somePartOfThePagesView">
  <!--
  This would be replaced with the content of the page "ThisIsAPage".
  For convenience if no page exists text noting that and a link to the page are provided so you can quickly add content.
  Note: replacement is not recursive. Triple brackets in Pages filling in values for the Page view are not replaced with Pages content.
  -->
  {{{ThisIsAPage}}}
</div>
```

All changes are stored in local storage provided by the Amplify API. This will use Local Storage if possible, UserData if in IE, and lastly try to pack your changes into a cookie if all else fails.

---

##Possible New Features##
* A way to backup the Pages store outside of the application. Trivial since it uses Backbone just need to create a backend.
* Any suggestions that seem reasonable.