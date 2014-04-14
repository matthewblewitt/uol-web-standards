# Measuring/Testing Performance & Support

## Browser support

It’s important to establish which browsers to officially support. Our own users are almost all that matters in deciding which browsers we officially support.

###Do websites need to look the same in every browser?

No. A page needs to serve its purpose in function and not appear broken. It’s not about browsers, it’s about serving the users of our software by delivering content that is valuable to them.

###What do we support?

We support current and previous versions of all modern browsers, IE8-9 & top-level modern mobile browsers with some reasonable amount of market share, but not beta or development versions. See below for a more comprehensive list (visit here for more info `browsehappy.com`. Browsers currently supported as of 11/04/2014:

####Desktop Browsers 

* Internet Explorer
  ** Supported: 8 to current version
  ** Explicitly unsupported: 7 and earlier & IE on Mac OS X
* Firefox
  ** Supported: 27 to current version
  ** Explicitly unsupported: 6 and earlier
* Chrome
  ** Supported: 32 to current version
* Safari
  ** Supported: 5 to current version
* Opera
  ** Supported: 12 to current version
  ** Explicitly unsupported: 8 and earlier
* PlayStation 3/PSP/NetFront
  ** Unsupported
* Other
  ** Unsupported

####Mobile Browsers

* Android browser
  ** Supported: 4.x, 3.x, and 2.3 (current versions)
* Mobile Safari
  ** Supported: 5.0 and 5.1 (current versions)
* BlackBerry Browser
* Chrome
* Firefox Mobile
* Opera Mobile
* Opera Mini
* Windows Phone?

## Recommended debugging tools

  * Firefox > Firebug(http://getfirebug.com/)
  * Safari > Web Inspector
  * Google Chrome > Developer Tools
  * Opera: [Dragonfly](http://www.opera.com/dragonfly)
  * Internet Explorer 6-7: [Developer Toolbar](http://microsoft.com/downloads/details.aspx?familyid=E59C3964-672D-4511-BB3E-2D5E1DB91038)
  * Internet Explorer 8-10: [Developer Tools](http://msdn.microsoft.com/en-us/library/dd565625(v=VS.85).aspx)
  * JavaScript Verifier [JSLint](http://www.jslint.com)

## Page speed

Test the load time of that page, analyze it and find bottlenecks

  * [GTMetrix](http://gtmetrix.com/)
  * [Pingdom](http://tools.pingdom.com/fpt/)
  * [Hammerhead](http://stevesouders.com/hammerhead/) (Firefox plugin)
  * [YSlow](https://developer.yahoo.com/yslow/)
  * [Google Page Speed](https://developers.google.com/speed/pagespeed/?csw=1)

# Accessibility

WC3 list of [available tools](http://www.w3.org/WAI/ER/tools/complete)

## Screen readers

  * Mac: [VoiceOver](http://www.apple.com/uk/accessibility/osx/voiceover/) (built in, also in iOS)
  * Linux: [ORCA](https://live.gnome.org/Orca/)
  * Windows: [NVDA](http://community.nvda-project.org/)

## Online tools

  * [WAVE (Web Accessibility Evaluation Tool)](http://wave.webaim.org/) works in a similar way to the W3C HTML validator
  * [SPUR](http://www.spurapp.com/), test the visual design of the website. It allows you to apply a variety of effects - such as greyscale, high contrast and blur
  * [Color Oracle](http://colororacle.org/) Color Oracle is a free color blindness simulator for Window, Mac and Linux

## To Dos

Add Retina device testing? Image switching?
