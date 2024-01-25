---
layout: default
title: Dynamic DNS
permalink: /dynamicdns/
---

Two methods are used to deal with having dynamic IP address:

1 dyndns on isp modem router

this specifically required creating an account on "duckdns.org".
then specifying the domain name, user id and token on the router.
when ever the ISP assigned address changes, the duckdns entry gets updated.


2 ddclient and cloudflare 

this required :
- buying a domain name
- changing the registar to cloudflare
- creating an api token on cloudflare
- installing ddclient on a raspberry pi
- configuring ddclient to use the api token to update an A record in the domain in cloudflare, when the ISP assigned domain changes

more details coming soon
