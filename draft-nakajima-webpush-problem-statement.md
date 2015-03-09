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
  I-D.thomson-webpush-aggregate:
  API:
    target: "https://w3c.github.io/push-api/"
    title: "Web Push API"
    author:
      name: "Bryan Sullivan"
    author:
      name: "Eduardo Fullea"
    author:
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

# Introduction        {#intro}

The delivery of real-time events such as incoming calls or messages is an essential feature of mobile application and its platform. 
The Web Push {{I-D.thomson-webpush-http2}} protocol has been proposed to enable delierying the events required by W3C Web Push API {{API}}.

Also, emergency alerting is an apparently important feature of telecommunication network such as cellular networks, allowing the goverments or authorities to send a warnings of natural disaster or accident. 

In the cellular network, several emergency alerting mechanisms have been proposed and merged into Public Warning System(PWS) {{3GPP.22.268}}. PWS provides several functions for example:

- Able to broadcast Warning notifications to multiple devices simultaneously.
- Able to broadcast Warning notifications based on geographical information.
- Provides reliable, secure delivery of Warning notification over 3GPP system.

Addition to PWS in the WiFi network, IEEE 802.11u {{IEEE80211u}} has an emergency support which uses Common Alerting Protocol (CAP) {{CAP}}. 

At IETF, Atoca WG has worked for 

This document will describe various use cases and requirements of emergency notification system using Web Push.

# Terminology

In cases where normative language needs to be emphasized, this document back on
established shorthands for expressing interoperability requirements on
implementations: the capitalized words "MUST", "MUST NOT", "SHOULD" and "MAY".
The meaning of these is described in {{RFC2119}}.

# Problem Statement {#problem}
TODO: show why this draft is needed.

- 既存緊急通報のメカニズムは限定的な環境でしか動作しない
- 標準化されたアプリケーション通知のメカニズムが存在しない
- 独自の実装の例を挙げる
- メッセージフォーマットの事例を書く
- 緊急じゃなくても重要な通知を行う

## Emergency Notification

- ETWS case
- 802.11u case
- Yurekuru case
- Web-based Signage case

- CAP protocol
- Atoca WG

## Important Notification delivery
Application Important notification delivery e.g. rtcweb incoming call


