---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
keywords: []
description: ADFS 3.0 and WAP (Formerly ADFS Proxy) are super powerful and really should not be so darn difficult to debug.
datePublished: '2016-05-01T21:03:08.412Z'
dateModified: '2016-05-01T20:47:12.634Z'
title: ''
author:
  - name: ''
    url: ''
sourcePath: _posts/2016-05-01-adfs-slays-me.md
published: true
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
starred: true
url: adfs-slays-me/index.html
_type: Article

---
ADFS 3.0 and WAP (Formerly ADFS Proxy) are super powerful and really should not be so darn difficult to debug.

My issue is that they work...great...for a few days...then I start getting this Exception in my ADFS 3.0 server's Event Log:

> MSIS7042: The same client browser session has made '6' requests in the last '1' seconds

And the major kick in the pants, is that Googling is not reviewing any solutions that last.

The ADFS Server and Proxy run fine...for days...then suddenly the MSIS7042 shows up. I've checked ![](https://the-grid-user-content.s3-us-west-2.amazonaws.com/4ab37bca-f0c2-4558-82ab-22910ce8207f.png)

I am using an ADFS/Proxy config very similar to the classic ADFS 2.0 model above. The DNS entry for "adfs.myco.org" resolves _internally_ to the 10.18 address of my ADFS server and resolves _externally_ to the public IP, which is NATed to my WAP (ADFS Proxy), which is a **different computer **that is not on my network. 

It would be logical to believe the issue is related to bouncing my client machine from on and off my network/VPN, rather than a server config.

Ah! But then why would this also happen to client machines that are static inside the network? Client machines like the ADFS server itself. All internal servers know nothing of the external DNS for ADFS. So there goes that theory.

Oh the humanity!