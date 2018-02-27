Social Web Working group drafts
===============================

* Social Web Protocols:

* Activity Stream

* Webmention: provides an API for sending and receiving notifications when a
  relationship is created between two documents. It works when the two
documents are on different domains, thus serving as a federation protocol.

* Micropub

* ActivityPub: provides a JSON-based API for sending and receiving
  [ActivityStreams2] activities as notifications.


Notes from: http://w3c-social.github.io/social-web-protocols, the document is
an overview of specifications Social Web working group is working on.

* The URL to activitystream2 working draft is broken https://www.w3.org/TR/activitystreams

* Content is represented as AT2 json. All objects must have a url it can be paged.

* ActivityPub specifies streams

* ActivityPub uses HTTP post request for OUTBOX

* Micropub

* LDP: Linked Data Platform

Using all three it talks how to create content, update it, delete it,

Then it talks about how to Subcribe

* All these protocols in collection can be used to connect to existing social
  network and interoperate with them.

* Question: How many website uses these protocols: see status for hi5, xing and
  friendster

* It appears that LinkedIN is not using OpenSocial now.
  https://developer.linkedin.com/docs/rest-api

* It appears that OpenSocial Activity Stream is replaced by Activity Stream 2.0
  and the original OpenSocial Activity Stream is not maintained anymore.

There have been no update in the OpenSocial spec from April 2014

* hi5's developer page doesn't resolve

* Friendster doesnt' exist anymore


http://www.cnet.com/news/hi5-gives-high-five-to-opensocial-foundation-with-developer-platform-launch/#!

MicroFormats
============

SoLiD
=====

* The issue is multiple silos..

* Different APIs
* No interoperablity
* Zero control over data
* Identity is tightly coupled with each application. (OpenID relaxes that a bit)

* Decouple Server Data and Applications
* App no longer "run" on dedicated servers
* App no longer require authentication
* Generic, REST API for managing data (LDP)
* No application logic in the server!


Solid Offers decentralized:
* Identity
* Authentication
* Access control
* Generic (and RESTful) data API

The app can fetch data from multiple or single soruce


Solid Tutorials
===============



WebId
-----
WebID-TLS: It is different from OpenID and certificate is installed on my
browser than being a server

Web documents can identify users

It can be very problematic if every website users its own login and identity.

Use certificates like TLS certificates. Create a public private key, the
browser signs the public key and sends it back.

Doesn't need password

Can also work with hardware encryption devices.

<-- Copy the diargram if possible -->

Uses existing infrastructure

Not sure if the private key is being stored in the browser or at the server

Can be used with CryptoSticks

