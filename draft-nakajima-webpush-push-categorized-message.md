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
  RFC3864:

informative:
  I-D.thomson-webpush-http2:

--- abstract

The Web Push protocol provides a means of delivering the events to clients 
based on the registration made by the application.
This document describes extentions to that protocol that enables the 
categorized message delivery based on priority.

This allows an application to request that a web push server deliver the prioritized message to a registered client.

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

# Categorized push subscribe {#category}

A new header field "Push-Category" is provided in subscribe request to indicate priority of new subscription.

POST /subscribe/1G_GIPMorg_n-IrQvqZr6g HTTP/1.1
Host: push.example.net
Push-Category: Normal

The "Push-Category" HTTP header field is an OPTIONAL header field that, when used, indicates a priority of push subscription and its delivery.

The following categories are defined:

normal: "normal" 

important:

emergency:


# IANA Considerations

This document specifies the HTTP header field listed below, which has 
been added to the "Permanent Message Header Field Names" registry 
defined in {{RFC3864}}.

Header field: Push-Catagory
Applicable protocol: http
Status: standard
Auther/Change controller:
  IETF (iesg@ietf.org)
  Internet Engineering Task Force
Specification document(s): this specification
Related information: None

