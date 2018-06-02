Google stupidly named this feature “[URL-Tracker](http://src.chromium.org/viewvc/chrome/trunk/src/chrome/browser/google_url_tracker.cc?view=markup)” which sounds really awful. It’s really not, and they just picked a horrible name.

Basically the URL Tracker connects to three random sites. It does this to check your DNS configuration in order to tell whether your DNS tries to resolve error pages or if Chrome should. Nothing scary here and it’s handled in a very nice way.

The feature was removed in 2010 it got replaced with pre-cached/link prefetching.