---
title: Problem Statement and Requirements for Emergency Notification using Web Push
abbrev: Problem Statement and Requirements for Web Push
docname: draft-nakajima-webpush-problem-statement-latest
date: 2015
category: info
ipr: trust200902

stand_alone: yes
pi: [toc, sortrefs, symrefs]

author:
 -
    ins: H. Nakajima
    name: Hirotaka Nakajima
    organization: Keio University
    email: hiro@awa.sfc.keio.ac.jp

normative:
  RFC2119:

informative:
  I-D.thomson-webpush-http2:
  I-D.ietf-httpbis-http2:
  PushAPI:
    target: "https://w3c.github.io/push-api/"
    title: "Web Push API"
    author:
      ins: "B. Sullivan"
      name: "Bryan Sullivan"
    author:
      ins: "E. Fullea"
      name: "Eduardo Fullea"
    author:
      ins: "M. Ouwerkerk"
      name: "Michaël van Ouwerkerk"
  3GPP.22.268:
  CAP:
    title: "Common Alerting Protocol v1.2"
    date: 2010-07
    author:
      name: "Elysa Jones"
    author:
      name: "Jacob Westfall"
  IEEE80211u:
    title: "IEEE Standard for Information Technology-Telecommunications and information exchange between systems-Local and Metropolitan networks-specific requirements-Part II: Wireless LAN Medium Access Control (MAC) and Physical Layer (PHY) specifications: Amendment 9: Interworking with External Networks"
    date: 2011-02-25
    author:
      organization: "IEEE"


--- abstract

The Web Push protocol provides a means of delivering the events to clients based on the registration made by the application. 
Also, the emergency alert notification system has been developed and deployed widely with mobile phones or smartphones, but has not deployed to Web-only devices.

This document outlines various existing emergency alert notification system in other protocols and use cases with their requirements.

--- middle

# Introduction {#intro}

The delivery of real-time events such as incoming calls or messages is an essential feature of mobile application and its platform. 
The Web Push {{I-D.thomson-webpush-http2}} protocol has been proposed to enable delierying the events required by W3C Web Push API {{PushAPI}}.

Also, emergency alerting is an apparently important feature of telecommunication network such as cellular networks, allowing the goverments or authorities to send a warnings of natural disaster or accident. 

In the cellular network, several emergency alerting mechanisms have been proposed and merged into Public Warning System(PWS) {{3GPP.22.268}}. PWS provides several functions for example:

- Able to broadcast Warning notifications to multiple devices simultaneously.
- Able to broadcast Warning notifications based on geographical information.
- Provides reliable, secure delivery of Warning notification over 3GPP system.

Addition to PWS, some work has been made to distribute the emergency alerting notification on different network. In the WiFi network, IEEE 802.11u {{IEEE80211u}} has an emergency support which uses Common Alerting Protocol (CAP) {{CAP}}. Also, Atoca WG has worked for defining the secure alerting format to broadcast CAP-based alert over IP network.

Those previous contribuions have been made to develop the method to distribute an emergency alerting notification. 

This document will describe various use cases and requirements of emergency notification system using Web Push.

# Terminology

In cases where normative language needs to be emphasized, this document back on
established shorthands for expressing interoperability requirements on
implementations: the capitalized words "MUST", "MUST NOT", "SHOULD" and "MAY".
The meaning of these is described in {{RFC2119}}.

# Problem Statement {#problem}

## Issues on existing emergency alerting system

- Rely on specific underlaying technology (e.g. 3GPP, 802.11u)
- Geo-based notification

## Use case of Web Push Emergency Alerting Notification

- Web-based Signage
- OTT emergency alerting system (local goverment or authorities)

## Non-emergency, Important notification

- Incoming call
Non-emergency but important notification is required to 

# Security Consideration
TBD

# IANA Consideration
TBD

