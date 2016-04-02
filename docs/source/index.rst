.. RadioKit Engine documentation master file, created by
   sphinx-quickstart on Sat Apr  2 19:51:27 2016.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to RadioKit Engine's documentation!
===========================================

RadioKit Engine is a cloud computing platform for building multimedia, mainly
audio-oriented applications. You can think about it as of “Amazon Web Services
for Audio”.

Instead of building complicated infrastructure from scratch, you can take
existing “building blocks” and build your app on top of them. Then RadioKit takes
care about what’s hidden from the users, and you can focus on what is your core
business and brings the most value to your users.

Platform is API-oriented. That means that most of the functionality is available
only through programming interfaces. There are some user interfaces for management,
but they show only part of the potential.

The API is mostly based on the REST API convention; so all communication with
the system is done over HTTPS protocol, which is the most widely adopted Internet
application protocol in the world. Data is serialized as JSON. That makes it
effectively platform-independent, it does not matter what language or technology
different parts of the system use, as they talk to each other with universal protocol.

Pieces composing RadioKit Engine are built as micro services. There are several
backends responsible for various tasks. Technically speaking they are separate
applications (although still speaking with the same protocol). That allows us to
keep system modular, create derivatives that fit specific clients’ needs, use different
languages for different purposes and makes system more reliable.

As most broadcasting applications have demand of high availability, we run our
software only within credible, reliable datacentres and providers such as:

*	Heroku (the biggest Platform-as-a-Service platform, itself hosted at Amazon Web Services),
*	OVH (the biggest European datacentre),
*	Microsoft Azure (cloud computing platform from Microsoft).

It is however, possible to host it within users' datacentre if certain technical
requirements are met.

We utilize worldwide Content Delivery Network CloudFlare which provides us geocaching,
speed optimization, encryption and protects the whole infrastructure from DDoS attacks.

Contents
~~~~~~~~

.. toctree::
   :maxdepth: 2

   services
   support
