---
layout: custom-post
title: "SilverLight DevCamp Nugget #4"
date: 2007-11-16
categories: news technical
author: MrPhil
---

I'm running into some technical challenges with Visual Studio 2005 and SilverLight XAML files. The validation and Intellisense aren't working correctly for XAML files, and the WPF Designer doesn't understand SilverLight XML properly.

I had to right click my XAML file and tell it to open with the XML Editor in order to make all the errors go away. The designer keeps complaining about the "x:name" attribute, even though it's perfectly valid SilverLight markup.

Hopefully these issues will be resolved in Visual Studio 2008. Until then, we'll have to work around these limitations. Thanks, Digital Lord Gates!

---

*Imported from mrphilgames.com on {{ site.time | date: "%Y-%m-%d" }}*