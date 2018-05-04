#### Hardens Chromium and it's settings in the name of security

The goal of this project is to provide information (and an extension maybe?) to setup Chromium for maximum security. 

[![Twitter URL](https://img.shields.io/twitter/url/https/twitter.com/fold_left.svg?style=social&label=Follow%20%40CHEF-KOCH)](https://twitter.com/FZeven)
[![Say Thanks!](https://img.shields.io/badge/Say%20Thanks-!-1EAEDB.svg)](https://saythanks.io/to/CHEF-KOCH)
[![Discord](https://discordapp.com/api/guilds/204394292519632897/widget.png)](https://discord.me/NVinside)

### Chromium vs. Mozilla Firefox (needs to be updated!)

## Performance
* Chromium consumes a little bit more memory than Firefox, but starts up faster - Chromes kernel requires more ressources
* Chromium tends to make better use of multi-core systems, using separate processes for each tab. This feature is still in development on Firefox
* The browsers have competitive Javascript performance, but Firefox has better support for the newest javascript features

## Features
* Chromium generally supports the latest HTML features sooner
* Firefox generally supports the latest Javascript features sooner
* Both have mobile versions
* Both manage bookmarks
* Both have a useful dashboard startpage
* Firefox is more extensible
* There are countless themes and extensions, and there's an advanced Customize mode to change the placement of anything on the screen.
* Firefox has an advanced user profile system that's easy to backup
* Both support syncing browser data and preferences between multiple installations, including on mobile
* Firefox allows non-tabbed mode, Chromium does not
* Firefox allows traditional style menus, Chromium does not
* Chrome was the first browser which by default introduced adblocking without any extension ([Android Chrome version got it first](https://www.ghacks.net/2017/07/31/google-launches-adblocker-in-chrome-dev-and-canary-for-android/))

## Extension coverage
* Some extensions like e.g. Ghostery lacks features compared to the Mozilla version
* Chromium has a Downloadbar and limited support for Greasemonkey, Tapermonkey Userscripts by default
* The Firefox extension API is far more powerful than Chromium's; every part of the browser can be customized
* Mozilla adopted WebExtension API which technically can run Chrome/Firefox extensions but it's messy (atm)
* Both extension/theme/plugin stores getting daily scans to avoid malware
* WebKit/WebExtension seems the today's default

## Plug-ins
* Chromium and Firefox are both trying to deprecate the old insecure and buggy NPAPI plugin system. Chromium uses its own PPAPI system for Flash
* Firefox uses a secure Javascript-based library for reading PDFs
* ~~Firefox is developing a secure Javascript-based replacement for Flash called Shumway, but it's dropped since Flash is known to be dying~~

## Data privacy with default settings
* Firefox uses Yahoo as its default search engine in North America, and other search engines in other regions
* Chromium uses 'Google' as its default search engine
* Firefox Sync can be hosted on your own server, and uses a zero-knowledge architecture. Chrome Sync only syncs to Google servers but's encrypted.
* Both support private sessions where there is no history saved (private/incognito modes)

## Data privacy after user configuration
* Both Firefox and Chromium extensions may send private/usage data to somewhere (with prior warning)
* You can change the default search engines of both to services like DuckDuckGo
* Users can easily disable features of Chromium that remotely use Google-services
* You can selectively enable Chromium's extensions for private sessions
* You can use NoScript in Firefox and µMatrix (formerly HTTP Switchboard) in Firefox and Chromium to greatly enhance your privacy
* Both support the HTTPS Everywhere extension from the Electronic Frontier Foundation
* Both can be configured to use TOR, but the TOR project recommends configuring Firefox or using the Firefox-based Tor browser
* Firefox allows extensive control over which elements of the browser run and transmit data. These can be changed in the about:config page
* Newer versions of Chromium require you download extensions from the Chrome web store or manually install from a local file
* None browser is perfect this is due -> we still using outdated protocols and usability


## Preferences file

See this [documentation](https://chromium.googlesource.com/chromium/src/+/master/docs/user_data_dir.md) for more details regarding to the default profiles.

Windows: C:\Users\<username>\AppData\Local\Google\Chrome\User Data\
MacOS X: ~/Library/Application Support/Google/Chrome/
Linux: ~/.config/google-chrome/


## Media Engagement Index (MEI) (Chrome 66+)

The MEI is determined by a ratio of visits to significant media playback events per origin, determined by these four factors:

* Consumption of the media (audio/video) must be greater than 7 seconds.
* Audio must be present and unmuted.
* Tab with video is active.
* Size of the video (in px) must be greater than 200×140.

## Chrome's Ads blocker

[Google](https://blog.chromium.org/2018/02/how-chromes-ad-filtering-works.html) is evaluating sites based on the [Better Ads standards](https://www.betterads.org/standards) and then rating them as a pass, warning, or failing. Site owners can access these evaluations using an API, and sites can be re-reviewed after bad ads have been addressed.


## Acknowledgements and References
* [Chrome might remove the enable_webrtc=false flag](https://bugs.chromium.org/p/chromium/issues/detail?id=800653)
* [Official System Hardening Guide](https://sites.google.com/a/chromium.org/dev/chromium-os/chromiumos-design-docs/system-hardening)
* [Official Chromium Security tracker](https://bugs.chromium.org/p/chromium/issues/list?q=Type%3DBug-Security)
* [Transitioning from SPDY to HTTP/2](https://blog.chromium.org/2016/02/transitioning-from-spdy-to-http2.html)
* [Chrome Vs. Chromium](http://www.linuxinsider.com/story/79510.html)
* [The Private Life of Chromium Browsers](https://thesimplecomputer.info/the-private-life-of-chromium-browsers)
* [How Chromium works](https://medium.com/@aboodman/in-march-2011-i-drafted-an-article-explaining-how-the-team-responsible-for-google-chrome-ships-c479ba623a1b#.is7blrj34)
* [BetterFirefox](https://github.com/CHEF-KOCH/BetterFirefox)
* [Chromium WPAD detection](https://sunweavers.net/blog/node/37)
* [Baselines of Web Browsers](https://thesimplecomputer.info/baselines-web-browsers)
* [Custom DNS names in Chromium](http://michaelkc.tumblr.com/post/98129633274/working-with-custom-dns-names-in-chromium)
* [Compile Chrome on Windows](https://github.com/henrypp/chromium)
* [POTARC](https://github.com/CHEF-KOCH/Online-Privacy-Test-Resource-List)
* [NoScript whitelist](https://github.com/CHEF-KOCH/NoScript-Whitelist)
* [Why isn't passive browser fingerprinting (including passive cookies) in Chrome's threat model?](https://dev.chromium.org/Home/chromium-security/security-faq#TOC-Why-isn-t-passive-browser-fingerprinting-including-passive-cookies-in-Chrome-s-threat-model-) *[ref](https://dev.chromium.org/Home/chromium-security/client-identification-mechanisms)
* [Browser Sec Whitepaper](https://github.com/cure53/browser-sec-whitepaper)
* [Chromium Updater Script by mkorthof](https://github.com/mkorthof/chrupd)
