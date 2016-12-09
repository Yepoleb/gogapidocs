Account Management
==================

Methods used to manage the user's account.

User
----

.. http:get:: /userData.json

    Information about the logged in user.

    .. sourcecode:: http

        GET /userData.json HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "country": "AT",
          "currencies": [
            {
              "code": "EUR",
              "symbol": "€"
            },
            {
              "code": "USD",
              "symbol": "$"
            }
          ],
          "selectedCurrency": {
            "code": "EUR",
            "symbol": "€"
          },
          "preferredLanguage": {
            "code": "en",
            "name": "English"
          },
          "ratingBrand": "PEGI",
          "isLoggedIn": true,
          "checksum": {
            "cart": null,
            "games": "c1fc44f3808bd755560e1b00d34451a1",
            "wishlist": "fcfd279ac1042f8baf8e659729ab1b89",
            "reviews_votes": null,
            "games_rating": null
          },
          "updates": {
            "messages": 0,
            "pendingFriendRequests": 0,
            "unreadChatMessages": 0,
            "products": 0,
            "forum": 0,
            "total": 0
          },
          "userId": "48628349971017",
          "username": "Yepoleb",
          "email": "mail@example.com",
          "personalizedProductPrices": [],
          "personalizedSeriesPrices": []
        }

.. http:get:: /user/changeCurrency/(str:currency)

    Changes the default currency.

    :param currency: One of the available currency codes from
                     :http:get:`/userData.json`
    :type currency: str

    **Example request**:

    .. sourcecode:: http

        GET /user/changeCurrency/EUR HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}

.. http:get:: /user/changeLanguage/(str:language)

    Changes the used locale.

    :param language: Language to use, possible values: en, de, fr, ru, pt
    :type language: str

    **Example request**:

    .. sourcecode:: http

        GET /user/changeLanguage/de HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}

.. http:get:: /user/set-redirect-url

    Sets URL to redirect to after login. You shouldn't need this with a native
    client which is always logged in.

    :query url: Redirect URL, the only accepted value seems to be ``checkout``

    **Example request**:

    .. sourcecode:: http

        GET /user/set-redirect-url?url=checkout HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    No content

.. http:get:: /user/reviewTipsStatus.json

    Checks if the user has read the tips that pop up before you can write your
    first review.

    **Example request**:

    .. sourcecode:: http

        GET /user/reviewTipsStatus.json HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "userId": "48628349971017",
          "readTips": false
        }

.. http:get:: /users/info/(int:user_id)

    Returns the public information about a user.

    **Example request**:

    .. sourcecode:: http

        GET /user/reviewTipsStatus.json HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "id": "48628349971017",
          "username": "Yepoleb",
          "userSince": 1449237763,
          "avatars": {
            "small": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_avs.jpg",
            "small2x": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_avs2.jpg",
            "medium": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_avm.jpg",
            "medium2x": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_avm2.jpg",
            "large": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_avl.jpg",
            "large2x": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_avl2.jpg"
          },
          "chatStatus": {
            "url": "https://embed.gog.com/u/Yepoleb/chat",
            "isChatRestricted": false
          }
        }

.. http:get:: /user/(int:user_id)/block

    TODO

.. http:get:: /user/(int:user_id)/unblock

    TODO


Games
-----


.. http:get:: /user/data/games.json

    List of games the account owns.

    **Example request**:

    .. sourcecode:: http

        GET /user/data/games HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "owned": [
            1207658691,
            1207658713,
            1207658805,
            1207658924,
            1207658930,
            1207658945,
            1207658957,
            1929434313,
            1949616134,
            1432207890,
            1444035366,
            1444036272,
            1443696086
          ]
        }

.. http:get:: /account/gameDetails/(int:game_id).json

    Returns detailed information about a game.

    **Example request**:

    .. sourcecode:: http

        GET /account/gameDetails/1207658691.json HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "title": "Unreal Tournament 2004 Editor's Choice Edition",
          "backgroundImage": "//images-4.gog.com/ebed1d5546a4fa382d7d36db8aee7f298eac7db3a8dc2f4389120b5b7b3155a9",
          "cdKey": "",
          "textInformation": "",
          "downloads": [
            [
              "English",
              {
                "windows": [
                  {
                    "manualUrl": "/downlink/unreal_tournament_2004_ece/en1installer3",
                    "downloaderUrl": "gogdownloader://unreal_tournament_2004_ece/installer_win_en",
                    "name": "Unreal Tournament 2004 Editor's Choice Edition (Part 1 of 3)",
                    "version": null,
                    "date": "",
                    "size": "1 MB"
                  },
                  {
                    "manualUrl": "/downlink/unreal_tournament_2004_ece/en1installer4",
                    "downloaderUrl": "gogdownloader://unreal_tournament_2004_ece/installer_win_en",
                    "name": "Unreal Tournament 2004 Editor's Choice Edition (Part 2 of 3)",
                    "version": null,
                    "date": "",
                    "size": "1.5 GB"
                  },
                  {
                    "manualUrl": "/downlink/unreal_tournament_2004_ece/en1installer5",
                    "downloaderUrl": "gogdownloader://unreal_tournament_2004_ece/installer_win_en",
                    "name": "Unreal Tournament 2004 Editor's Choice Edition (Part 3 of 3)",
                    "version": null,
                    "date": "",
                    "size": "507 MB"
                  }
                ]
              }
            ]
          ],
          "extras": [
            {
              "manualUrl": "/downlink/file/unreal_tournament_2004_ece/6093",
              "downloaderUrl": "gogdownloader://unreal_tournament_2004_ece/6093",
              "name": "manual (33 pages)",
              "type": "manuals",
              "info": 1,
              "size": "2 MB"
            },
            {
              "manualUrl": "/downlink/file/unreal_tournament_2004_ece/6073",
              "downloaderUrl": "gogdownloader://unreal_tournament_2004_ece/6073",
              "name": "HD wallpapers",
              "type": "wallpapers",
              "info": 12,
              "size": "115 MB"
            },
            {
              "manualUrl": "/downlink/file/unreal_tournament_2004_ece/6083",
              "downloaderUrl": "gogdownloader://unreal_tournament_2004_ece/6083",
              "name": "avatars",
              "type": "avatars",
              "info": 8,
              "size": "1 MB"
            }
          ],
          "dlcs": [],
          "tags": [],
          "isPreOrder": false,
          "releaseTimestamp": 1227585600,
          "messages": [],
          "changelog": null,
          "forumLink": "https://embed.gog.com/forum/unreal_series",
          "isBaseProductMissing": false,
          "missingBaseProduct": null
        }

.. http:get:: /user/wishlist.json

    Returns the wishlist of the account.

    **Example request**:

    .. sourcecode:: http

        GET /user/wishlist.json HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "wishlist": {
            "1207658750": true,
            "1207658928": true,
            "1207658986": true,
            "1207659002": true,
            "1207659023": true,
            "1437553673": true,
            "1440407371": true,
            "1452863689": true,
            "1893001152": true,
            "1948823323": true
          },
          "checksum": "e7c70b9b758318ed2f08b4450272296c"
        }

.. http:get:: /user/wishlist/add/(int:game_id)

    Adds a game to the wishlist and returns the new list.

    **Example request**:

    .. sourcecode:: http

        GET /user/wishlist/add/1207658750 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    See :http:get:`/user/wishlist.json`

.. http:get:: /user/wishlist/remove/(int:game_id)

    Removes a game from the wishlist and returns the new list.

    **Example request**:

    .. sourcecode:: http

        GET /user/wishlist/remove/1207658750 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    See :http:get:`/user/wishlist.json`

.. http:get:: /user/games_rating.json

    Returns the game the account has rated. Rating numbers are stars * 10

    **Example request**:

    .. sourcecode:: http

        GET /user/games_rating.json HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "games_rating": {
            "1207658957": 40,
            "1207659032": 50
          },
          "checksum": "175d07086bff9322646f1dad2749483e"
        }

.. http:get:: /user/review_votes.json

    Returns review IDs the user has voted on.

    **Example response**:

    .. sourcecode:: http

        GET /user/review_votes.json HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "reviews": [
            123456,
            1112223
          ],
          "checksum": "76c03aa67251e46db3271adf4641b815"
        }

Friends
-------

.. http:get:: /friends/remove/(int:user_id)

    TODO

.. http:get:: /friends/invite/(int:user_id)

    TODO

.. http:get:: /friends/invites/(int:user_id)/accept

    TODO

.. http:get:: /friends/invites/(int:user_id)/decline

    TODO
