---
title: Categorized Message for Web Push
abbrev: Web Push Categorized Message
docname: draft-nakajima-webpush-push-categorized-message-latest
date: 2015
category: std
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



--- abstract

The Web Push protocol provides a means of delivering the events to clients 
based on the registration made by the application.
This document describes extentions to that protocol that enables the 
categorized message delivery based on priority.

This allows an application to request that a web push server deliver the emergency message to a registered client.

--- middle

# Introduction        {#intro}

The delivery of the prioritized message, especially emergency message, is a common feature of push notification services.
This document describes a mechanism based on the Web Push protocol {{I-D.thomson-webpush-http2}}.

A new header field is added to the Web Push push response message. This header field identifies a category that lets push server delivering message with priority. Application can use the category to send a push message with priority.

# Terminology

In cases where normative language needs to be emphasized, this document back on
established shorthands for expressing interoperability requirements on
implementations: the capitalized words "MUST", "MUST NOT", "SHOULD" and "MAY".
The meaning of these is described in {{RFC2119}}.

# Categorized push subscribe

A new push "subscribe"  


