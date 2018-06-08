## Overview

[QUIC](https://en.wikipedia.org/wiki/QUIC) is a new protocol developed by Google, like every other protocol there might be concerns regarding to privacy.

## Concerns

* Might bypasses DNS
* Preconnections done

## Truth

The Chromium and Chrome team is in general highly interested in fixing security related concerns, as shown in the official bugtracker these guys working on it, since Chrome 67 the issue is partially resolved.

This has nothing much to do with 'spyware' or bypassing something in order to deliver ads, it's a new protocol (by default disabled in Chromium) which of course needs some more tests and bugfixed in more recent Browser versions.

Since we disabled link prediction you should not see any third-party connections on for example YouTube to googleads.g.doubleclick.net behind the blocker. I've tested this since v65 and it does show nothing unusual.

* https://blog.brave.com/quic-in-the-wild-for-google-ad-advantage/
* https://bugs.chromium.org/p/chromium/issues/detail?id=715140#c11
* https://bugzilla.mozilla.org/show_bug.cgi?id=1158011
* https://github.com/diracdeltas/quic-request