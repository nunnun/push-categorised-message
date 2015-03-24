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
    date: 2015-02
    author:
      organization: "W3C"
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
  SignageUseCase:
    title: "Web-based Signage Scenarios and Use Cases"
    author: 
      name: "Futomi Hatano"
      ins: "F. Hatano"
    target: "http://www.w3.org/community/websignage/wiki/Web-based_Signage_Use_cases_and_Requirements"
    date: 2013-01
  Geofencing:
    title: "Enhanced Geolocation"
    author:
      name: "Giridhar Mandyam"
      ins: "G. Mandyam"
    target: "https://gmandyam.github.io/enhanced-geolocation/"
    date: 2014-08-23


--- abstract

The Web Push protocol provides a means of delivering the events to clients based
on the registration and resource subscription made by the application. Also, the
emergency alert notification system has been developed and deployed widely with
mobile phones or smartphones, but has not deployed to Web-only devices.

This document outlines various existing emergency alert notification system in
other protocols and use cases with their requirements.

--- middle

# Introduction {#intro}

The delivery of real-time events such as incoming calls or messages is an
essential feature of mobile application and its platform.  The Web Push
{{I-D.thomson-webpush-http2}} protocol has been proposed to enable delivering
the events required by W3C Web Push API {{PushAPI}}.

Also, emergency alerting is an apparently important feature of telecommunication
network such as cellular networks, allowing the governments or authorities to
send a warnings of natural disaster or accident. 

This document will describe various use cases and requirements of emergency
notification system using Web Push.

# Terminology

In cases where normative language needs to be emphasized, this document back on
established shorthands for expressing interoperability requirements on
implementations: the capitalized words "MUST", "MUST NOT", "SHOULD" and "MAY".
The meaning of these is described in {{RFC2119}}.

# Problem Statement {#problem}

## Issues on existing emergency alerting system

This section describes the survey and issues of existing emergency alerting
system.

In the cellular network, several emergency alerting mechanisms have been
proposed and merged into Public Warning System(PWS) {{3GPP.22.268}}. PWS
provides several functions for example:

- Able to broadcast Warning notifications to multiple devices simultaneously.
- Able to broadcast Warning notifications based on geographical information.
- Provides reliable, secure delivery of Warning notification over 3GPP system.

Addition to PWS, some work has been made to distribute the emergency alerting
notification on different network. In the WiFi network, IEEE 802.11u
{{IEEE80211u}} has an emergency support which uses Common Alerting Protocol
(CAP) {{CAP}}. Also, Atoca WG has worked for defining the secure alerting format
to broadcast CAP-based alert over IP network.

Those previous contributions have been made to develop the method to distribute
an emergency alerting notification.  However, those systems require a specific
access network such as 3GPP or WiFi. There is an issue that desktop device or
device not equipped with 3GPP or WiFi is not able to receive an emergency
alerting notification.

The second issue is geolocation-aware system.  A major emergency alert such as
an earthquake or a tsunami is distributed at geolocation specific area based on
the cellular cell or WiFi cell. Web Push relies on HTTP/2
{{I-D.ietf-httpbis-http2}} which relies on IP network.  Geofencing
{{Geofencing}} is discussed in W3C Geolocation WG to let the application to
interact with the loose location-aware computation without knowing device's
exact location. However, geofencing needs device's support, Web Push emergency
alerting notification system has to have a mechanism to detect device's
location to send a location specific alerts.

## Use case of Web Push Emergency Alerting Notification

There are two potential use case of Web Push Emergency Alerting notification. 

The first use case is a Web-based Signage. Digital signage has widely deployed
among the world. Signages located at public area such as train station or street
play a significant role in natural disaster or accident by providing the
evacuation alert or correct informations. Recent few years W3C worked on
Web-based signage which has Web browser is embedded, allowing to display or play
Web content. Disaster use case is proposed in W3C Web-based Signage Scenarios
and Use Cases {{SignageUseCase}}. 

The second use case is an over-the-top emergency alerting system operated by a
local authorities or a government. An emgergency alerting of an major natural
disaster such as an earthquake or a tsunami could be distributed by existing
emergency alerting system (e.g. PWS). However, distributing an emergency
alerting of an minor natual disaster such as heavy rain alert using existing
method is too complicated compared to the importance of the information or
alert. Web Push emergency alerting notification can provide more specific alert
or information requested by the mobile or desktop application not requiring 3GPP
or WiFi network. For example:

- Raining alert based on the location
- Transit alert such as accident information or suspend.

## Non-emergency, Important notification

Non-emergency but important notification is required to real-time applications.
Real-time application such as VoIP or telecommunication application, need to
deliver the notification faster than other notification. 

# Security Consideration
Discovery of Push Server and application is out of scope in this document.
However, discovery of reliable Push Server and application is definitely
important. Also, it is important for Web Push Emergency Alerting notification to
have a mechanism to avoid the abuse of system.

# IANA Consideration
TBD

