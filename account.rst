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

    :query str expand: Additional sections to request. Possible values:
        friendStatus, wishlistStatus, blockedStatus

    :resjson int friendStatus.status:

        * ANONYMOUS_USER = 0: No special relationship with this user.
        * INVITED_USER = 1: You have sent this user a friend request.
        * INVITED_BY_USER = 2: You have received a friend request from this user.
        * FRIEND = 3: You are friends with this user.

    :resjson int friendStatus.dateCreated: Timestamp of when a friend request
        was sent or ``null``.

    :resjson int friendStatus.dateAccepted: Timestamp of when a friend request
        was accepted or ``null``.

    :resjson int wishlistStatus.sharing:

        * WISHLIST_PRIVATE = 0
        * WISHLIST_PUBLIC = 1
        * WISHLIST_FOR_FRIENDS = 2

    **Example request**:

    .. sourcecode:: http

        GET /users/info/48628349971017?expand=friendStatus,wishlistStatus,blockedStatus HTTP/1.1
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
          "friendStatus": {
            "id": "48628349971017",
            "status": 0,
            "dateCreated": null,
            "dateAccepted": null
          },
          "wishlistStatus": {
            "sharing": 2,
            "url": "https://embed.gog.com/u/Yepoleb/wishlist"
          },
          "blockedStatus": {
            "blocked": false
          },
          "chatStatus": {
            "url": "https://embed.gog.com/u/Yepoleb/chat",
            "isChatRestricted": false
          }
        }


Games & Movies
--------------

.. http:get:: /user/data/games

    List of games and movies the account owns. Use
    :http:get:`/account/getFilteredProducts` for more than just the IDs.

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

    Returns detailed information about a game. Seems to work with movies as
    well, but they have their own method.

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

.. http:get:: /account/movieDetails/(int:movie_id).json

    Returns detailed information about a movie.

    **Example request**:

    .. sourcecode:: http

        GET /account/movieDetails/1207665463.json HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "title": "Art of Playing, The",
          "backgroundImage": "//images-1.gog.com/a3e48e4e370e2e7e9cdf648b712ff0506b994b404b64993e3fab4934294a4890",
          "cdKey": "",
          "textInformation": "",
          "downloads": [
            {
              "manualUrl": "/downlink/the_art_of_playing/en1video1",
              "downloaderUrl": "gogdownloader://the_art_of_playing/video_en1video1",
              "playerUrl": "http://www.gog.com/video/the_art_of_playing/en1video1",
              "name": "The Art of Playing (1080p)",
              "size": "1.1 GB"
            },
            {
              "manualUrl": "/downlink/the_art_of_playing/en1video2",
              "downloaderUrl": "gogdownloader://the_art_of_playing/video_en1video2",
              "playerUrl": "http://www.gog.com/video/the_art_of_playing/en1video2",
              "name": "The Art of Playing (720p)",
              "size": "382 MB"
            },
            {
              "manualUrl": "/downlink/the_art_of_playing/en1video3",
              "downloaderUrl": "gogdownloader://the_art_of_playing/video_en1video3",
              "playerUrl": "http://www.gog.com/video/the_art_of_playing/en1video3",
              "name": "The Art of Playing (576p)",
              "size": "163 MB"
            }
          ],
          "extras": [
            {
              "manualUrl": "/downlink/file/the_art_of_playing/34143",
              "downloaderUrl": "gogdownloader://the_art_of_playing/34143",
              "name": "wallpaper",
              "type": "wallpapers",
              "info": 1,
              "size": "1 MB"
            },
            {
              "manualUrl": "/downlink/file/the_art_of_playing/34213",
              "downloaderUrl": "gogdownloader://the_art_of_playing/34213",
              "name": "trailer",
              "type": "video",
              "info": 1,
              "size": "92 MB"
            },
            {
              "manualUrl": "/downlink/file/the_art_of_playing/34553",
              "downloaderUrl": "gogdownloader://the_art_of_playing/34553",
              "name": "subtitles (English)",
              "type": "game add-ons",
              "info": 1,
              "size": "1 MB"
            },
            {
              "manualUrl": "/downlink/file/the_art_of_playing/37973",
              "downloaderUrl": "gogdownloader://the_art_of_playing/37973",
              "name": "subtitle pack",
              "type": "game add-ons",
              "info": 1,
              "size": "1 MB"
            }
          ],
          "dlcs": [],
          "tags": [],
          "isPreOrder": false,
          "releaseTimestamp": 693612000,
          "messages": [],
          "changelog": null,
          "forumLink": "https://www.gog.com/forum/movies",
          "isBaseProductMissing": false,
          "missingBaseProduct": null
        }

.. http:get:: /user/games_rating.json

    Returns the products the account has rated. Rating numbers are stars * 10

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

    **Example request**:

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

.. http:post:: /account/hideProduct/(int:product_id)

    Hides a product from your library.

    **Example request**:

    .. sourcecode:: http

        POST /user/hideProduct/1430740458 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}

.. http:post:: /account/revealProduct/(int:product_id)

    Unhides a product from your library.

    **Example request**:

    .. sourcecode:: http

        POST /user/revealProduct/1430740458 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}


Wishlist
--------

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

.. http:get:: /user/wishlist/add/(int:product_id)

    Adds a product to the wishlist and returns the new list.

    **Example request**:

    .. sourcecode:: http

        GET /user/wishlist/add/1207658750 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    Same as :http:get:`/user/wishlist.json`

.. http:get:: /user/wishlist/remove/(int:product_id)

    Removes a product from the wishlist and returns the new list.

    **Example request**:

    .. sourcecode:: http

        GET /user/wishlist/remove/1207658750 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    Same as :http:get:`/user/wishlist.json`


Tags
----

.. http:post:: /account/tags/attach

    Adds a tag to a product.

    :query int product_id: Product ID to add the tag to
    :query int tag_id: ID of the tag to attach

    **Example request**:

    .. sourcecode:: http

        POST /account/tags/attach?product_id=1430740458&tag_id=301045732 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "success": true
        }

.. http:post:: /account/tags/detach

    Removes a tag to a product.

    :query int product_id: Product ID to remote the tag from
    :query int tag_id: ID of the tag to detach

    **Example request**:

    .. sourcecode:: http

        POST /account/tags/detach?product_id=1430740458&tag_id=301045732 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "success": true
        }

.. http:post:: /account/tags/add

    Creates a new tag.

    :query str name: Name of the new tag

    **Example request**:

    .. sourcecode:: http

        POST /account/tags/add?name=MYTAG HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "id": "301045732"
        }

.. http:post:: /account/tags/delete

    Deletes a tag.

    :query int tag_id: ID of the tag to delete

    **Example request**:

    .. sourcecode:: http

        POST /account/tags/delete?tag_id=301045732 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "status": "deleted"
        }

.. http:post:: /account/tags/update

    Updates the tag list. Data isn't actually posted but included as a
    query parameter *(wat!?)*.

    :query json tags: URL-encoded json data of the tags

    **Example request**:

    .. sourcecode:: http

        POST /account/tags/update?tags=%5B%7B%22id%22:%22301045732%22... HTTP/1.1
        Host: embed.gog.com

    **Example request data**:

    This is the urldecoded content of the query parameter.

    .. sourcecode:: json

        [{
          "id": "372082953",
          "name": "MYTAG"
        }, {
          "id": "243982903",
          "name": "COMPLETED",
          "productCount": "12"
        }, {
          "id": "243982893",
          "name": "NEXT TO PLAY",
          "productCount": "4"
        }, {
          "id": "243982883",
          "name": "BACKLOG",
          "productCount": "0"
        }, {
          "id": "243982873",
          "name": "FAVORITE",
          "productCount": "0"
        }]

    **Example response**:

    .. sourcecode:: json

        {
          "status": "updated"
        }


Settings
--------

.. http:get:: /account/save_birthday/(str:date)

    Sets the birthday.

    :param date: Date in ISO 8601 format

    **Example request**:

    .. sourcecode:: http

        GET /account/save_birthday/2000-12-31 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}

.. http:get:: /account/save_country/(str:country)

    Sets the country.

    :param country: Country as ISO 3166 code

    **Example request**:

    .. sourcecode:: http

        GET /account/save_country/AT HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}

.. http:get:: /account/save_newsletter_subscription/(bool:subscribed)

    Enable notifications for releases and announcements.

    :param subscribed: 0 (unsubscribe), 1 (subscribe)

    **Example request**:

    .. sourcecode:: http

        GET /account/save_newsletter_subscription/1 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}

.. http:get:: /account/save_promo_subscription/(bool:subscribed)

    Enable notifications for promos and deals.

    :param subscribed: 0 (unsubscribe), 1 (subscribe)

    **Example request**:

    .. sourcecode:: http

        GET /account/save_promo_subscription/1 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}

.. http:get:: /account/save_wishlist_notification/(bool:subscribed)

    Enable notifications for whishlist items on sale.

    :param subscribed: 0 (unsubscribe), 1 (subscribe)

    **Example request**:

    .. sourcecode:: http

        GET /account/save_wishlist_notification/1 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}

.. http:get:: /account/save_sharing_wishlist/(int:privacy)

    Sets if the wishlist is public.

    :param privacy: Can be 0 (nobody), 1 (everyone) or 2 (friends only)

    **Example request**:

    .. sourcecode:: http

        GET /account/save_sharing_wishlist/1 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}

.. http:get:: /account/save_chat_privacy/(int:privacy)

    Sets the chat privacy setting.

    :param privacy: Can be 0 (nobody), 1 (anyone) or 2 (friends only)

    **Example request**:

    .. sourcecode:: http

        GET /account/save_chat_privacy/1 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}

.. http:get:: /account/save_search_privacy/(bool:privacy)

    Changes if the user can be found by name or email.

    :param privacy:

        * 0 (search disabled)
        * 1 (search enabled)

    **Example request**:

    .. sourcecode:: http

        GET /account/save_search_privacy/1 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}

.. http:post:: /account/logout_all_sessions

    **Example request**:

    .. sourcecode:: http

        GET /account/logout_all_sessions HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}

.. http:get:: /user/changeCurrency/(str:currency)

    Changes the default currency.

    :param currency: ISO 4217 currency code, currently available: USD, EUR,
        GBP, AUD, RUB, PLN, CAD, CHF, NOK, SEK and DKK. Please only use the
        ones listed in :http:get:`/userData.json`.
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

    :param language: Language to use, possible values: de-DE, en-US, fr-FR,
        pt-BR, ru-RU, zh-Hans
    :type language: str

    **Example request**:

    .. sourcecode:: http

        GET /user/changeLanguage/de HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}

.. http:post:: /account/save_shelf_background/(str:background_name)

    Sets the library shelf style.

    :param background_name: One of wood, mate_black, glass, chrome, white,
        piano_black.
    :type background_name: str

    **Example request**:

    .. sourcecode:: http

        GET /account/save_shelf_background/glass HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {}

.. http:post:: /account/avatar

    Upload a profile avatar. This request uses the login.gog.com domain
    instead of the regular gog.com.

    **Example request**:

    .. sourcecode:: http

        POST /account/avatar HTTP/1.1
        Host: login.gog.com

        Content-Disposition: form-data; name="files[]"; filename="avatar.png"
        Content-Type: image/png

    **Example response**:

    .. sourcecode:: json

        {
          "avatars": {
            "small": "https:\/\/images.gog.com\/d7d8e3ed8ad2d9fd3557c83c4237a913b14e621c84e21fab594a9d961cd98fe4_avs.jpg",
            "small_2x": "https:\/\/images.gog.com\/d7d8e3ed8ad2d9fd3557c83c4237a913b14e621c84e21fab594a9d961cd98fe4_avs2.jpg",
            "medium": "https:\/\/images.gog.com\/d7d8e3ed8ad2d9fd3557c83c4237a913b14e621c84e21fab594a9d961cd98fe4_avm.jpg",
            "medium_2x": "https:\/\/images.gog.com\/d7d8e3ed8ad2d9fd3557c83c4237a913b14e621c84e21fab594a9d961cd98fe4_avm2.jpg",
            "large": "https:\/\/images.gog.com\/d7d8e3ed8ad2d9fd3557c83c4237a913b14e621c84e21fab594a9d961cd98fe4_avl.jpg",
            "large_2x": "https:\/\/images.gog.com\/d7d8e3ed8ad2d9fd3557c83c4237a913b14e621c84e21fab594a9d961cd98fe4_avl2.jpg"
          }
        }


Friends
-------

.. http:post:: /friends/search

    Search for GOG users.

    **Example request**:

    .. sourcecode:: http

        POST /friends/search HTTP/1.1
        Host: embed.gog.com

        {
          "query": "Yepoleb"
        }

    **Example response**:

    .. sourcecode:: json

        {
          "id": "48628349971017",
          "galaxyUserId": "48628349957132247",
          "username": "Yepoleb",
          "userSince": 1449237763,
          "avatars": {
            "small": "https:\/\/images.gog.com\/d7d8e3ed8ad2d9fd3557c83c4237a913b14e621c84e21fab594a9d961cd98fe4_avs.jpg",
            "small2x": "https:\/\/images.gog.com\/d7d8e3ed8ad2d9fd3557c83c4237a913b14e621c84e21fab594a9d961cd98fe4_avs2.jpg",
            "medium": "https:\/\/images.gog.com\/d7d8e3ed8ad2d9fd3557c83c4237a913b14e621c84e21fab594a9d961cd98fe4_avm.jpg",
            "medium2x": "https:\/\/images.gog.com\/d7d8e3ed8ad2d9fd3557c83c4237a913b14e621c84e21fab594a9d961cd98fe4_avm2.jpg",
            "large": "https:\/\/images.gog.com\/d7d8e3ed8ad2d9fd3557c83c4237a913b14e621c84e21fab594a9d961cd98fe4_avl.jpg",
            "large2x": "https:\/\/images.gog.com\/d7d8e3ed8ad2d9fd3557c83c4237a913b14e621c84e21fab594a9d961cd98fe4_avl2.jpg"
          }
        }

.. http:get:: /friends/invite/(int:user_id)

    Send a friend invite to a user. **Warning: Response is not an object and
    may break certain JSON decoders.**

    **Example request**:

    .. sourcecode:: http

        POST /friends/invite/17081829469374 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        "ok"

.. http:get:: /friends/remove/(int:user_id)

    Removes a friend from your friends list. **Warning: Response is not an
    object and may break certain JSON decoders.**

    **Example request**:

    .. sourcecode:: http

        POST /friends/remove/17081829469374 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        "ok"

.. http:get:: /friends/invites/(int:user_id)/accept

    Accepts a friend invite. **Warning: Response is not an object and
    may break certain JSON decoders.**

    **Example request**:

    .. sourcecode:: http

        POST /friends/invites/17081829469374/accept HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        "ok"

.. http:get:: /friends/invites/(int:user_id)/decline

    Declines a friend invite. **Warning: Response is not an object and
    may break certain JSON decoders.**

    **Example request**:

    .. sourcecode:: http

        POST /friends/invites/17081829469374/decline HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        "ok"

.. http:get:: /users/(int:user_id)/block

    Block communication from a user. **Warning: Response is not an object and
    may break certain JSON decoders.**

    **Example request**:

    .. sourcecode:: http

        POST /friends/17081829469374/block HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        "ok"

.. http:get:: /users/(int:user_id)/unblock

    Unblock communication from a user. **Warning: Response is not an object and
    may break certain JSON decoders.**

    **Example request**:

    .. sourcecode:: http

        POST /friends/17081829469374/unblock HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        "ok"
