---
layout: post
title: "HTTP2 for Project Managers"
excerpt: "A Transition Plan for HTTP2"
tags: [HTTP2, project]
image:
# feature: pic data center slice 1900x500.jpg
  feature: https://cloud.githubusercontent.com/assets/300046/14622043/8b1f9cce-0584-11e6-8b9f-4b6db5bb6e37.jpg
  credit: 
  creditlink: 
comments: true
---
<i>{{ page.excerpt }}</i>
<hr />

{% include _toc.html %}


There are many blogs and YouTube videos about the technical details and configuration changes associated with HTTP/2. But I haven’t seen much in the way of the 
<strong>implications</strong> to project managers and other management personnel
who need to make real the transition. So I rearranges the various technical facts here, with PROTIPs identifying suggestions.

## Googling #

PROTIP: An inclusive Google search would involve several keywords.

Try this search phrase:

   <pre>
   http/2 or h2 or http2 or http_2 or rfc7540
   </pre>

   "HTTP/2" seems to be the most frequent keyword returned.

   Alternatives to the special character slash is needed with
   the <a target="_blank" href="https://twitter.com/http_2">
   @HTTP_2</a> Twitter handle used by 
   <a target="_blank" href="http://http2.github.io">
   http://http2.github.io</a>, the home page for HTTP/2
   maintained by the <a target="_blank" href="https://httpwg.github.io/">
   IETF HTTP Working Group</a>.

   rfc7540 is the industry specification, at
   <a target="_blank" href="http://httpwg.org/specs/rfc7540.html">
   http://httpwg.org/specs/rfc7540.html</a>
   and
   <a target="_blank" href="https://tools.ietf.org/html/rfc7540">
   http://tools.ietf.org/html/rfc7540</a>.

   "h2" is the value of the response in the HTTP header:

   `ALPH protocol: h2`

BTW, ALPN, or Application-Layer Protocol Negotiation, is a TLS extension that includes the protocol negotiation within the exchange of hello messages. 
See https://tools.ietf.org/html/rfc7301

TODO: Confirm whether HTTP2 ALPN is actually activated on in the web server under test.


## Web Scanners #

Some organizations use web protocol scanners as an aspect of quality.

The W3C scanner identifies issues such as "https" being specified instead of "http"
and the inclusion of a slash at the end of URLs to avoid a redirect.

ALPN negotiates which protocol should be handled over a secure connection in a way that is more efficient and avoids additional round trips. 
So with HTTP2, `HTTP://` can be specified and the connection will still be encrypted as if you entered `https://`.

Will the W3C scanner recognize this change?
If you need to explain what W3C finds,
you would need to add this to your notes about the discrepancy.


## Adoption Statistics #

Several websites respond with whether a domain name you input supports HTTP2:

   * <a target="_blank" href="https://spdycheck.org/">
   https://spdycheck.org</a>

   * <a target="_blank" href="https://tools.keycdn.com/http2-test">
   https://tools.keycdn.com/http2-test</a>

Among <a target="_blank" href="https://w3techs.com/technologies/details/ce-http2/all/all"> sites supporting http2:

   * Home pages of organizations that support HTTP2:
google, youtube, facebook, twitter, instagram, wikipedia, yahoo, dropbox, wordpress.

   * Home pages of organizations that do not yet support HTTP2 (as of June 6, 2016):
amazon, github.com, github.io, ibm, microsoft, sap, salesforce, spotify, pandora, paypal

PROTIP: It doesn’t matter much that industry-wide only 
8% of all websites are supporting HTTP2.
Even though support for HTTP2 may be lacking,
IT organizations nevertheless need to begin preparing for its adoption
because customers and vendors and partners are getting onboard.
Ideally, IT organizations ought to get "in front" of people in the organization who need to experiment with that eventuality. Don’t hold them back.

PROTIP: Include in adoption not just HTTP2 but SPDY, its predecessor.

## Data center prep. #

TODO: Every component needs to be analyzed for its impact on HTTP2 adoption.

PROTIP: The presence of legacy data center components is often the most vexing block to HTTP2
adoption because of the lead time necessary for changes to occur.

PROTIP: Those who develop programs assuming HTTP2 may need to use a cloud vendor which supports HTTP2
while the corporate data center catches up.

#### Load balancers #

* https://support.f5.com/kb/en-us/products/big-ip_ltm/manuals/product/ltm-implementations-11-6-0/21.html

#### CDNs #

The Cloudflare CDN was an early adopter of HTTP2.

But getting the Akamai CDN to support can be complex:

   * <a target="_blank" href="https://http2.akamai.com/">
    https://http2.akamai.com</a> mentions 

   * <a target="_blank" href="https://community.akamai.com/community/web-performance/blog/2015/01/26/enabling-http2-h2-in-akamai">THis blog</a>
   suggests: 

   TODO: Check whether H2 is part of your Akamai contract.

   * Akamai Web Experience product (like Ion, Alta, WAA, DSA, and RMA) with HTTPS enabled
   is needed to support HTTP2?


#### Proxies #

Many proxies don’t usually speak full, compliant HTTP1 let alone HTTP2.

This needs to change.



## Browsers #

The use of "evergreen" browsers is a pre-requisite for HTTP2 adoption.

But most "enterprise" organizations tend to use Microsoft browsers 
and lag behind in upgrades of operating systems.

<a target="_blank" href="http://caniuse.com/#feat=http2">
http://caniuse.com/#feat=http2</a> 
says Microsoft did not support HTTP2 in IE until IE11 with in Windows 10
(and Server 2016).
Microsoft is said to be developing their own 
"Microsoft Speed + Mobility (Microsoft S+M)" protocol.

The Chrome browser is the first to support HTTP2 because the company
created SPDY on which HTTP2 is based.

PROTIP: To encourage its use, IT organizations need to make the installation 
of Chrome browsers a part of the standard process for getting laptops ready for users. This includes making Chrome the default browser.

There is 
<a target="_blank" href="https://chrome.google.com/webstore/detail/http2-and-spdy-indicator/mpbpobfflnpcgagjijhmgnchggcjblin?hl=en">
a Chrome plug-in</a>
that shows an icon to show whether a site is HTTP2.

Put this in the address bar of a Chrome browser to see which tab supports "h2":

   * <a target="_blank" href="chrome://net-internals/#http2">
   chrome://net-internals/#http2"

The Mozilla browser is lagging behind in support of HTTP2:

   <a target="_blank" href="https://wiki.mozilla.org/Networking/http2">
   https://wiki.mozilla.org/Networking/http2</a>


## Performance Testing #

PROTIP: A pragmatic approach to adoption is that if the <strong>overall</strong>
performance improves, use it, then tune away.

But that strategy assumes that one has a way to determine what performance is
before and after.

PROTIP: Measure the impact of incremental changes to individual
configuration settings and components. Change one aspect at a time and measure
impact to a baseline.

PROTIP: Upgrade performance testing tools before measuring baselines.
This avoids a risk that different versions of the tool introduce bias.

Most performance testing tools work by emulating browsers.
So whatever technique is used in new browsers need to be programmed into
the tool. And that’s not an easy job. So differences are bound to occur.

Programs that emulate browsers need to add, among other features, 
the capability to handle <strong>binary streams</strong> 
rather than just text handling in HTTP1.1.
This difference is part of the speed improvement in HTTP2.

Those who use LoadRunner need the latest version, 12.53 which became available in June, 2016. See <a target="_blank" href="http://community.hpe.com/t5/LoadRunner-and-Performance/How-to-gain-the-best-from-LoadRunner-s-support-of-HTTP-2/ba-p/6863547#.V1Yp7ZMrJZo">this blog</a>.

Those who use JMeter need the 
<a target="_blank" href="https://github.com/syucream/jmeter-http2-plugin">
jmeter-http2-plugin</a> sampler.


## Server Installs #

A big part of the speed improvement offered by HTTP2 over HTTP1 is
compression of HTTP headers.

Legacy "enterprise" web applications tend to have large headers to 
pass cookies back and forth. So just this alone may provide a boost to
performance.

PROTIP: Install HPACK (from Twitter) from
<a target="_blank" href="https://github.com/twitter/hpack">
https://github.com/twitter/hpack</a>


#### Apache

Apache mod_h2 was unofficial 

This should appear:

   <tt>
   mod_http2 (v1.0.0, nghttp2 1.3.4), initializing...
   </tt>

nghttp2.org

httpd.conf

   * https://icing.github.io/mod_h2/howto.html

   * https://icing.github.io/mod_h2/howto.html#chrome


#### NGNIX 

* nginx 9 still in beta?


## Programming changes #

Previous hacks to obtain more speed now need to be dismantled 
because HTTP2 made them unnecessary.

In fact, previous hacks are now <strong>technical debt</strong> because
they cause HTTP2 to be slower.

* <a target="_blank" href="https://www.youtube.com/watch?v=CSjL1lrNAx4">
HTTP 203: HTTP2 (S3, Ep7)</a>
to me is the most entertaining video on developer’s transition to HTTP2
("This is like Monty Python meets HTTP/2﻿").

* <a target="_blank" href="https://www.youtube.com/watch?v=yURLTwZ3ehk">
Yesterday's perf best-practices are today's HTTP/2 anti-patterns - Velocity 2015 (Santa Clara)</a> on YouTube dives into the issues
Ilya Grigorik (@igrigorik) also has a 
<a target="_blank" href="https://docs.google.com/presentation/d/1r7QXGYOLCh4fcUq0jDdDwKJWNqWK1o4xMtYpKZCJYjM/present?slide=id.p19"> slidedeck</a>
and
<a target="_blank" href="http://www.oreilly.com/webops-perf/free/files/HTTP2-high-perf-browser-networking.pdf
free 29 page book with diagrams</a>
that explains the nitty gritty of HTTP2.


### Sprites #

To reduce the number of files being downloaded, 
programmers have been arranging several icons into a single file and
using CSS to present a section of the image file.

This time-consuming hack
is no longer necessary with HTTP2 because HTTP2 uses a single TCP connection
and streams any number of files simultaneously.

<a target="_blank" href="https://www.usenix.org/sites/default/files/conference/protected-files/nsdi14_slides_wang.pdf"> In this PDF</a>
Xiao Wang's benchmarks
found that most of the performance from SPDY comes from the single TCP connection. 

   * http://wprof.cs.washington.edu/spdy


### Tiles #

Previously with HTTP1, large files were split into small tiles
for the HTML or CSS code to assemble.

   * <a target="_blank href="http://http2.golang.org/gophertiles?latency=0"
   see it live</a>

The site is demo’d by Brad Fitzpatrick in
<a target="_blank" href="https://www.youtube.com/watch?v=FARQMJndUn0">
this YouTube video</a> and
<a target="_blank" href="https://docs.google.com/presentation/d/1G9gPIAorTsVD_pMgEJcTGEjt5ApZZWyI2uO244_f7TU/present?slide=id.p">
slide deck</a> shows his demo site:

### Domain sharding #

Domain sharding hurts performance under HTTP2.


## Size of objects and line quality matters #

https://www.usenix.org/sites/default/files/conference/protected-files/nsdi14_slides_wang.pdf

HTTP/SPDY takes longer with large objects transmitted over lines with loss.

This was confirmed by http://wprof.cs.washington.edu/spdy


## TLS certificates #

2) TLS certificates (not SSL certificates) used on servers

* delivery certificate needs to have Perfect Forward Secrecy (PFS) support enabled in TLS metadata



## Other Resources 

https://ma.ttias.be/architecting-websites-http2-era/

https://ma.ttias.be/http2



