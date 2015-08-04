# Introduction #

Maturity Models have popped up from time to time, and they attempt to measure a system's (or part of a system's) adherence to some standard, like the RESTful architectural style.

This page tries to detail different ways of measuring how well a client matches up on different axis.

# Details #

| Axis | Level 0  | Level 1 | Level 2 | Level 3 |
|:-----|:---------|:--------|:--------|:--------|
| [URLs](http://www.bizcoder.com/index.php/2012/03/07/hypermedia-client-maturity-model/) | HTTP RPC (mints URLs) | Fragile, Fragmented | Supple  | Reactive (uses links) |
| Media Types | Unused   | ?       | ?       | Drives the client |
| Caching | No caching | Respect caching directives | Conditional requests | "Browser" cache |
| Stateless | Stores state | ?       | ?       | Stateless |
| Code-on-demand | No code-on-demand | ?       | ?       | Does code-on-demand |
| Uniform interface | ?        | ?       | ?       | Adheres strictly to to the uniform interface |
| Authentication | Proprietary? | Cookies? | OAuth?  | BASIC/DIGEST? |
| Other axis | ?        | ?       | ?       |?        |

# About each axis #

## URLs ##

If the client mints all of its URLs itself, or if it uses links found in responses to achieve its goals.  If it uses links, then its

## Media Types ##

Does the client know or care about media types?

### Level 0 ###
Client doesn't know or care about media types, always parses the response according to a hard coded set of rules based on what the goal of the request was.

### Level 3 ###

All responses are understood according to their media type, regardless of what state the client component might be in.  The client component handles all responses with the same grace.

## Uniform Interface ##

Is the client using custom headers or custom methods?

### Level 0 ###

Uses proprietary headers to achieve certain goals.

### Level 3 ###

Operates strictly within the set of documented and de facto standards.  Uses HTTP extension headers when these are standardized

## Caching ##

What does the client do when it comes to caching?

TODO: maybe split this up into two "axis" one for request headers, and the other for the client side cache?

### Level 0 ###

The client itself employs no caches, and does not care about any caching headers

### Level 3 ###

The client contains a browser cache that remembers the state of the client component to provide "back button" functionality.  The Cache-Control and Expires headers are honored.