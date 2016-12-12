GOG Connect
===========

.. http:get:: /api/v1/users/(int:user_id)/gogLink/steam/linkedAccount

    Returns information about accounts linked through GOG connect.

    **Example request**:

    .. sourcecode:: http

        GET /api/v1/users/48628349971017/gogLink/steam/linkedAccount HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "href": "https://embed.gog.com/api/v1/users/48628349971017/gogLink/steam/linkedAccount",
          "user": {
            "status": "linked",
            "gogUsername": "Yepoleb",
            "gogAvatar": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d",
            "steamUsername": "Yepoleb",
            "steamAvatar": "https://steamcdn-a.akamaihd.net/steamcommunity/public/images/avatars/be/beed19c0f5dcf844ca2b89cacce7ed49a2729e7b_medium.jpg"
          },
          "exchangableSteamProducts": "https://embed.gog.com/api/v1/users/48628349971017/gogLink/steam/exchangeableProducts"
        }

.. http:get:: /api/v1/users/(int:user_id)/gogLink/steam/exchangeableProducts

    Returns list of product IDs currently on GOG Connect and whether they are
    available to claim.

    **Example request**:

    .. sourcecode:: http

        GET /api/v1/users/809081000454/gogLink/steam/exchangeableProducts HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "href": "https://www.gog.com/api/v1/users/809081000454/gogLink/steam/exchangeableProducts",
          "items": {
            "1207658744": {
              "id": 1207658744,
              "status": "imported"
            },
            "1207658796": {
              "id": 1207658796,
              "status": "readyToLink"
            },
            "1207658797": {
              "id": 1207658797,
              "status": "unavailable"
            },
          }
        }

.. http:get:: /api/v1/users/(int:user_id)/gogLink/steam/synchronizeUserProfile

    Instructs Connect to scan a user's Steam account for eligible games.

    **Example request**:

    .. sourcecode:: http

        GET /api/v1/users/48628349971017/gogLink/steam/synchronizeUserProfile HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    No content

.. http:get:: /api/v1/users/(int:user_id)/gogLink/steam/claimProducts

    Claims the available games.

    **Example request**:

    .. sourcecode:: http

        GET /api/v1/users/48628349971017/gogLink/steam/claimProducts HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    TODO
