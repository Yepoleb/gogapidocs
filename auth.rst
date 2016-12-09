Authentication
==============

Introduction
------------

All GOG APIs support token authorization, similar to OAuth2. The web domains 
`www.gog.com <https://www.gog.com>`_, `embed.gog.com <https://embed.gog.com>`_
and some of the Galaxy domains support session cookies too. They both have to
be obtained using the GOG login page, because a CAPTCHA may be required to
complete the login process.

Auth-Flow
---------

1. First you need a web server to receive the login code. I'm running a Python 
   HTTPServer on my local machine, but anything that supports dynamically 
   generated content should work. The url for it is http://localhost:8000/token.

2. Send the user to https://auth.gog.com/auth and use the url to your web server
   as redirect url. More details about the parameters of this request are
   described below.

3. Once the login process is completed, the user should be redirected to your
   server with a login "code" appended to the url. Take that code and use it to
   request a token.

4. Renew the token when it expires after about an hour. Check the original
   response for an accurate lifetime.

Authorizing a Request
---------------------

To authorize a request set the ``Authorization`` header to ``Bearer <token>``. This
has to be done for each call.

**Example request**:

.. sourcecode:: http

    GET /library/windows HTTP/1.1
    Host: embed.gog.com
    Authorization: Bearer xpIjnwyncascjBf20yz1n1tu8jo9spxyvy3zlvlL0rfoiiuly2hu5xnfgjysnuyhjqI7cmcatscp3ybgDjeqzwCggttnombuuicn_t6dbqybzYvpoieqtamaKuxpgclnUlt_q4jf_haj2emwgtrkzdlkhwinu7o93bpxWrbjdxr

Methods
-------

.. http:get::  /auth

    Redirects to the login site. Don't use this directly from your client, it's
    not a JSON API, visit it with a web browser instead.

    :query str client_id: OAuth2 Client ID. Use ``46899977096215655`` until we know
        how to get our own IDs.
    :query str redirect_id: Your redirect url that will receive the login code.
    :query str response_type: Use ``code``
    :query str layout: Use ``client2``

    **Example request**:
    
    .. sourcecode:: http
    
        GET /auth?client_id=46899977096215655&redirect_uri=http%3A%2F%2Flocalhost%3A8000%2Ftoken&response_type=code&layout=client2 HTTP/1.1
        Host: auth.gog.com

    **Example redirect**:
    
    .. sourcecode:: none
    
        http://localhost:8000/token?code=oF8OSgZVMFb7a8Y3Dolrz4YPqDUnG7TCTsekYKcWnFNcmWWCJH7XJS3RN9d9NB0slx4FS1kss-llBEXvgkCX8oNTP1u3yYG1p56f35jVZCclrCQMk803k5LmQLKM1Wb7

.. http:get:: /token

    Generates a new auth token from a login code or refreshes an old one.

    :query str client_id:
        OAuth2 client ID. Use ``46899977096215655``
    :query str client_secret:
        OAuth2 secret. Use 
        ``9d85c43b1482497dbbce61f6e4aa173a433796eeae2ca8c5f6129f2dc4de46d9``
    :query str grant_type:
        ``authorization_code`` for new logins, ``refresh_token`` for refreshs.
    :query str code:
        **Only for new logins:** Login code you got from the auth redirect.
    :query str redirect_uri:
        **Only for new logins:** The redirect URL you used in the auth request.
    :query str refresh_token:
        **Only for refreshes:** The refresh_token you got from an old token. This
        is a separate entry, not the old access token.
    
    **Example request**:
    
    .. sourcecode:: http
    
        GET /token?client_id=46899977096215655&client_secret=9d85c43b1482497dbbce61f6e4aa173a433796eeae2ca8c5f6129f2dc4de46d9&grant_type=authorization_code&code=oF8OSgZVMFb7a8Y3Dolrz4YPqDUnG7TCTsekYKcWnFNcmWWCJH7XJS3RN9d9NB0slx4FS1kss-llBEXvgkCX8oNTP1u3yYG1p56f35jVZCclrCQMk803k5LmQLKM1Wb7&redirect_uri=http%3A%2F%2Flocalhost%3A8000%2Ftoken HTTP/1.1
        Host: auth.gog.com
    
    **Example response**:
    
    .. sourcecode:: json
    
        {
          "expires_in": 3600,
          "scope": "",
          "token_type": "bearer",
          "access_token": "xpIjnwyncascjBf20yz1n1tu8jo9spxyvy3zlvlL0rfoiiuly2hu5xnfgjysnuyhjqI7cmcatscp3ybgDjeqzwCggttnombuuicn_t6dbqybzYvpoieqtamaKuxpgclnUlt_q4jf_haj2emwgtrkzdlkhwinu7o93bpxWrbjdxr",
          "user_id": "48628349957132247",
          "refresh_token": "48il-pjxfpknX0hwtxvBnRgNr-n5JAOTKpczaLEBHW7F65iTchjO46f7I-HAV-Cb",
          "session_id": "6354900816570477251"
        }
