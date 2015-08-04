# Introduction #
This article sets forth a list of features that should be present in any toolkit, library, and/or framework that supports REST.

# REST Implementation Toolkit #

The ease and fidelity of a REST-ful HTTP implementation depends, in part, on the quality of the programming tools at the developers disposal. This article identifies eight programming elements needed to support REST-ful HTTP implementations and why they are important. The author also provides examples of how these elements appear in common programming languages.

Finally, several examples of patterns and anti-patterns in programming are reviewed with an eye toward the impact developer toolkits have in making it easier or more difficult to successfully build a REST-ful HTTP implementation.

_NOTE: Consider both client and server issues when describing these essential programming elements._

| **Feature** | **Description** |
|:------------|:----------------|
| Request Dispatcher | Routes HTTP requests to the proper execution code |
|  URI Handler | Parses the details of the URI (scheme, path, query info, etc.) and exposes them for use. |
| Mime Parser | Handles the details of determining the media type including support for conneg |
| Request Handler | Target of the Request Dispatcher; the interesting/computational stuff goes here |
| Representation Handler | Converts stored data into the proper representation for responses and handles incoming representations from requests |
| HTTP Client | A 'mini HTTP Client' that allows you to make requests to, and handle responses from, other HTTP servers |
| Caching     | Basic support for caching and conditional requests |
| Authentication | Understands various auth models (Basic, Digest, OAuth, etc. |