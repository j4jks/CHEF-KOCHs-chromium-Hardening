#### Hardens Chromium and it's settings in the name of security


### Chromium vs. Firefox

## Performance
* Chromium consumes a little bit more memory than Firefox, but starts up faster.
* Chromium tends to make better use of multicore systems, using separate processes for each tab. This feature is still in development on Firefox.
* The browsers have competitive Javascript performance, but Firefox has better support for the newest javascript features.

## Features
* Chromium generally supports the latest HTML features sooner.
* Firefox generally supports the latest Javascript features sooner.
* Both have mobile versions.
* Both manage bookmarks
* Both have a useful dashboard startpage
* Firefox is more extensible.
* There are countless themes and extensions, and there's an advanced Customize mode to change the placement of anything on the screen.
* Firefox has an advanced user profile system that's easy to backup
* Both support syncing browser data and preferences between multiple installations, including on mobile.
* Firefox allows non-tabbed mode, Chromium does not
* Firefox allows traditional style menus, Chromium does not.

## Extension coverage
* There's Adblock and Flashblock for both
* Ghostery lacks some blockage on Chromium
* Chromium has a Downloadbar and limited support for Greasemonkey, Tapermonkey Userscripts by default.
* The Firefox extension API is far more powerful than Chromium's; every part of the browser can be customized.

## Plug-ins
* Chromium and Firefox are both trying to deprecate the old insecure and buggy NPAPI plugin system. Chromium uses its own PPAPI system for Flash.
* Firefox uses a secure Javascript-based library for reading PDFs.
* Firefox is developing a secure Javascript-based replacement for Flash called Shumway, but's dropped since Flash is known to be dying.

## Data privacy with default settings
* Firefox uses Yahoo as its default search engine in North America, and other search engines in other regions.
* Chromium uses Google as its default search engine
* Firefox Sync can be hosted on your own server, and uses a zero-knowledge architecture. Chrome Sync only syncs to Google.
* Both support private sessions where there is no history saved

## Data privacy after user configuration
* Both Firefox's and Chromium's extensions may send private/usage data to somewhere (with prior warning)
* You can change the default search engines of both to services like DuckDuckGo.
* Users can easily disable features of Chromium that remotely use Google-services
* You can selectively enable Chromium's extensions for private sessions
* You can use NoScript in Firefox and µMatrix (formerly HTTP Switchboard) in Firefox and Chromium to greatly enhance your privacy
* Both support the HTTPS Everywhere extension from the Electronic Frontier Foundation.
* Both can be configured to use TOR, but the TOR project recommends configuring Firefox or using the Firefox-based Tor browser
* Firefox allows extensive control over which elements of the browser run and transmit data. These can be changed in the about:config page
* Newer versions of Chromium require you download extensions from the Chrome web store or manually install from a local file.

## Other stuff
* [Official Chromium Security tracker](https://bugs.chromium.org/p/chromium/issues/list?q=Type%3DBug-Security) - I'm official supporter/commiter now :)
* [Transitioning from SPDY to HTTP/2](https://blog.chromium.org/2016/02/transitioning-from-spdy-to-http2.html)
* [Chrome Vs. Chromium](http://www.linuxinsider.com/story/79510.html)
* [The Private Life of Chromium Browsers](https://thesimplecomputer.info/the-private-life-of-chromium-browsers)
* [How Chromium works](https://medium.com/@aboodman/in-march-2011-i-drafted-an-article-explaining-how-the-team-responsible-for-google-chrome-ships-c479ba623a1b#.is7blrj34)
* [BetterFirefox](https://github.com/CHEF-KOCH/BetterFirefox)
* [Chromium WPAD detection](https://sunweavers.net/blog/node/37)
* [Baselines of Web Browsers](https://thesimplecomputer.info/baselines-web-browsers)
* [Custom DNS names in Chromium](http://michaelkc.tumblr.com/post/98129633274/working-with-custom-dns-names-in-chromium)