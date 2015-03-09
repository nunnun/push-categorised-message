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
  RFC3864:

informative:
  I-D.thomson-webpush-http2:
  I-D.ietf-httpbis-http2:
  I-D.thomson-webpush-aggregate:
  API:
    target: https://w3c.github.io/push-api/
    title: "Web Push API"
  TS22168:
    title: "Earthquake and Tsunami Warning System (ETWS) requirements"
    date: 2008-06
    author:
      organization: "3GPP"

--- abstract

The Web Push protocol provides a means of delivering the events to clients based on the registration made by the application. 
Also, the emergency alert notification system has been developed and deployed widely with mobile phones or smartphones, but has not deployed to Web-only devices.

This document outlines various existing emergency alert notification system in other protocols and use cases with their requirements.

--- middle

# Introduction        {#intro}

The delivery of real-time events such as incoming calls or messages is an essential feature of mobile application and its platform. 
The Web Push {{I-D.thomson-webpush-http2}} protocol has been proposed to enable delierying the events required by W3C Web Push API {{API}}.

Also, emergency alerting is an apparently important feature of telecommunication network such as cellular networks, allowing the goverments or authorities to send a warnings of natural disaster or accident. 
In the cellular network, Earthquake and Tsunami Warning System {{TS22168}} has been developed and deployed 

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

- CAP protocol
- Atoca WG

## Important Notification delivery
Application Important notification delivery e.g. rtcweb incoming call

# Categorized push subscription {#category}

A new header field "Push-Category" is provided in subscribe request to indicate priority of new subscription.

~~~~~~~~~~
POST /subscribe/1G_GIPMorg_n-IrQvqZr6g HTTP/1.1
Host: push.example.net
Push-Category: Normal
~~~~~~~~~~
{: #figxmpstore title="Example of push subscribe request with Push-Category header"}

The "Push-Category" HTTP header field is an OPTIONAL header field that, when used, indicates a priority of push subscription and its delivery.

The following categories are defined:

normal: "normal" category indicates that push subscription 

important: "important" category indicates that push channel MUST be delivered prior to "normal" push channel. Application MUST send a push message with stream which has a higher weight compared to Default stream priorities defined at {{I-D.ietf-httpbis-http2}}.

~~~~~~~~~~
    +-------+           +--------------+       +-------------+
    |  UA   |           | Push Service |       | Application |
    +-------+           +--------------+       +-------------+
        |                      |                      |
        |      Register        |                      |
        |--------------------->|                      |
        |       Monitor        |                      |
        |<====================>|                      |
        |      Subscribe       |                      |
        |--------------------->|                      |
        |           Provide Subscription              |
        |-------------------------------------------->|
        |                      |                      |
        :                      :                      :
        |                      |     Push Message     |
        |                      | with PRIORITY header |
        |    Push Message      |<---------------------|
        |<---------------------|                      |
        |                      |                      |
~~~~~~~~~~

emergency: "emergency" category indicates that push channel MUST be delivered prior to any other categorized or uncategorized push channel. User Agent MUST send a aggregated channel creation request {{I-D.thomson-webpush-aggregate}}. Application MUST send a push message with stream which has a highest weight compared to other stream on the connection.

~~~~~~~~~~
    +-------+           +--------------+       +-------------+
    |  UA   |           | Push Service |       | Application |
    +-------+           +--------------+       +-------------+
        |                      |                      |
        |      Register        |                      |
        |--------------------->|                      |
        |       Monitor        |                      |
        |<====================>|                      |
        |      Subscribe       |                      |
        | (Aggregated Channel) |                      |
        |--------------------->|                      |
        |           Provide Subscription              |
        |-------------------------------------------->|
        |                      |                      |
        :                      :                      :
        |                      |     Push Message     |
        |                      | with PRIORITY header |
        |    Push Message      |<---------------------|
        |<---------------------|                      |
        |                      |                      |
~~~~~~~~~~

# Security Considerations

# IANA Considerations

This document specifies the HTTP header field listed below, which has 
been added to the "Permanent Message Header Field Names" registry 
defined in {{RFC3864}}.

~~~~~~~~~~
Header field: Push-Catagory
Applicable protocol: http
Status: standard
Auther/Change controller:
  IETF (iesg@ietf.org)
  Internet Engineering Task Force
Specification document(s): this specification
Related information: None
~~~~~~~~~~

