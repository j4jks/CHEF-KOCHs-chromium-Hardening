## Overview
Google added support for a feature known as _asynchronous DNS_ to Google Chrome, which aims to speed up page loading times by resolving the IP address of a website before you click the link. 

## How does it work?
It works by scanning a web page as it loads, finding any domain names linked and using a Domain Name Server (DNS) to find the IP address associated with each of them. Google says it should respect the DNS server that the user has configured on-device, but on some occasions, this seems not to be the case. Users are reporting that DNS based ad-blockers like Pi-hole no longer function correctly on the latest version of Chrome.

Keep in mind that Google officially works on this `issue` it's not really designed to bypass DNS based ad-blockers!
