Galaxy APIs
===========

api.gog.com
-----------

.. http:get:: /products/(int:product_id)

    Returns information about a product.

    :query str expand: Comma separated list of additional sections to request.
        Possible values: downloads, expanded_dlcs, description, screenshots,
        videos, related_products, changelog

    **Example request**:

    .. sourcecode:: http

        GET /products/1207658691?expand=downloads,expanded_dlcs,description,screenshots,videos,related_products,changelog HTTP/1.1
        Host: api.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "id": 1207658691,
          "title": "Unreal Tournament 2004 Editor's Choice Edition",
          "purchase_link": "https://www.gog.com/checkout/manual/1207658691",
          "slug": "unreal_tournament_2004_ece",
          "content_system_compatibility": {
            "windows": true,
            "osx": false,
            "linux": false
          },
          "languages": {
            "en": "English"
          },
          "links": {
            "purchase_link": "https://www.gog.com/checkout/manual/1207658691",
            "product_card": "https://www.gog.com/game/unreal_tournament_2004_ece",
            "support": "https://www.gog.com/support/unreal_tournament_2004_ece",
            "forum": "https://www.gog.com/forum/unreal_series"
          },
          "in_development": {
            "active": false,
            "until": null
          },
          "is_secret": false,
          "game_type": "game",
          "is_pre_order": false,
          "release_date": "2008-11-25T06:00:00+0200",
          "images": {
            "background": "//images-3.gog.com/ebed1d5546a4fa382d7d36db8aee7f298eac7db3a8dc2f4389120b5b7b3155a9.jpg",
            "logo": "//images-3.gog.com/b6fff8c1a9600816e8c250ec6959def0e996f960b8c5083fae313c242c63ed84_glx_logo.jpg",
            "logo2x": "//images-2.gog.com/b6fff8c1a9600816e8c250ec6959def0e996f960b8c5083fae313c242c63ed84_glx_logo_2x.jpg",
            "icon": "//images-1.gog.com/10604b810f6c7121fc7072a43a642d400047c25196ca171afef931f0064623ad.png",
            "sidebarIcon": "//images-2.gog.com/10604b810f6c7121fc7072a43a642d400047c25196ca171afef931f0064623ad_sbicon.png",
            "sidebarIcon2x": "//images-4.gog.com/10604b810f6c7121fc7072a43a642d400047c25196ca171afef931f0064623ad_sbicon_2x.png"
          },
          "dlcs": [],
          "downloads": {
            "installers": [
              {
                "id": "installer_windows_en",
                "name": "Unreal Tournament 2004 Editor's Choice Edition",
                "os": "windows",
                "language": "en",
                "language_full": "English",
                "version": null,
                "total_size": 2105540608,
                "files": [
                  {
                    "id": "en1installer3",
                    "size": 1048576,
                    "downlink": "https://api.gog.com/products/1207658691/downlink/installer/en1installer3"
                  },
                  {
                    "id": "en1installer4",
                    "size": 1572864000,
                    "downlink": "https://api.gog.com/products/1207658691/downlink/installer/en1installer4"
                  },
                  {
                    "id": "en1installer5",
                    "size": 531628032,
                    "downlink": "https://api.gog.com/products/1207658691/downlink/installer/en1installer5"
                  }
                ]
              }
            ],
            "patches": [],
            "language_packs": [],
            "bonus_content": [
              {
                "id": 6093,
                "name": "manual (33 pages)",
                "type": "manuals",
                "count": 1,
                "total_size": 2097152,
                "files": [
                  {
                    "id": 6093,
                    "size": 2097152,
                    "downlink": "https://api.gog.com/products/1207658691/downlink/product_bonus/6093"
                  }
                ]
              }
            ]
          },
          "expanded_dlcs": [],
          "description": {
            "lead": "",
            "full": "",
            "whats_cool_about_it": ""
          },
          "screenshots": [
            {
              "image_id": "de2a58c68c63b5a60603394ab8fdb4c66810807671d5985bce958c566a02ef08",
              "formatter_template_url": "https://images-4.gog.com/de2a58c68c63b5a60603394ab8fdb4c66810807671d5985bce958c566a02ef08_{formatter}.png",
              "formatted_images": [
                {
                  "formatter_name": "ggvgt",
                  "image_url": "https://images-3.gog.com/de2a58c68c63b5a60603394ab8fdb4c66810807671d5985bce958c566a02ef08_ggvgt.jpg"
                },
                {
                  "formatter_name": "ggvgt_2x",
                  "image_url": "https://images-2.gog.com/de2a58c68c63b5a60603394ab8fdb4c66810807671d5985bce958c566a02ef08_ggvgt_2x.jpg"
                },
                {
                  "formatter_name": "ggvgm",
                  "image_url": "https://images-2.gog.com/de2a58c68c63b5a60603394ab8fdb4c66810807671d5985bce958c566a02ef08_ggvgm.jpg"
                },
                {
                  "formatter_name": "ggvgm_2x",
                  "image_url": "https://images-2.gog.com/de2a58c68c63b5a60603394ab8fdb4c66810807671d5985bce958c566a02ef08_ggvgm_2x.jpg"
                },
                {
                  "formatter_name": "ggvgl",
                  "image_url": "https://images-2.gog.com/de2a58c68c63b5a60603394ab8fdb4c66810807671d5985bce958c566a02ef08_ggvgl.jpg"
                },
                {
                  "formatter_name": "ggvgl_2x",
                  "image_url": "https://images-4.gog.com/de2a58c68c63b5a60603394ab8fdb4c66810807671d5985bce958c566a02ef08_ggvgl_2x.jpg"
                }
              ]
            }
          ],
          "videos": [],
          "related_products": [],
          "changelog": null
        }

.. http:get:: /products/(int:product_id)/(str:dl_url)

    Returns secure url and chunklist for a file.

    **Example request**:

    .. sourcecode:: http

        GET /products/1207658691/downlink/installer/en1installer3 HTTP/1.1
        Host: api.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "downlink": "https://cdn.gog.com/secure/unreal_tournament_2004_ece/pc/setup_ut2004_2.0.0.6.exe?a3c669cc2530fcf96b5599c0b5ceeb6a8179fe593c36d93e3396d982826ae9b366853042adc7efdeed599f74be21ec6615c731f9d25fc1e95c2711d7782b7beb2686dcd53a64440c04be87da3549947b72d90f5365ffaf1efcd51b633fc6c621ab3394540348f5b669f30782673bcc251a965dc82f33148b7e852070027e20b5eb56e05c460bd099cf17db03e4a9bdc01255ffe32bfd4f41019e8e7150694a5c&fileExtForIe=.exe",
          "checksum": "https://cdn.gog.com/secure/unreal_tournament_2004_ece/pc/setup_ut2004_2.0.0.6.exe.xml?a3c669cc2530fcf96b5599c0b5ceeb6a8179fe593c36d93e3396d982826ae9b366853042adc7efdeed599f74be21ec6615c731f9d25fc1e95c2711d7782b7beb2686dcd53a64440c04be87da3549947b72d90f5365ffaf1efcd51b633fc6c621ab3394540348f5b669f30782673bcc251a965dc82f33148b7e852070027e20b5eb56e05c460bd099cf17db03e4a9bdc01255ffe32bfd4f41019e8e7150694a5c&fileExtForIe=.exe"
        }

    **Example chunklist**:

    .. sourcecode:: xml

        <file name="gog_tis_100_2.0.0.3.sh" available="1" notavailablemsg="" md5="8acedf66c0d2986e7dee9af912b7df4f" chunks="4" timestamp="2015-07-30 17:11:12" total_size="36717998">
            <chunk id="0" from="0" to="10485759" method="md5">7e62ce101221ccdae2e9bff5c16ed9e0</chunk>
            <chunk id="1" from="10485760" to="20971519" method="md5">b80960a2546ce647bffea87f85385535</chunk>
            <chunk id="2" from="20971520" to="31457279" method="md5">5464b4499cd4368bb83ea35f895d3560</chunk>
            <chunk id="3" from="31457280" to="36717997" method="md5">0261b9225fc10c407df083f6d254c47b</chunk>
        </file>



auth.gog.com
------------

See :doc:`/auth`


cfg.gog.com
-----------

.. http:get:: /desktop-galaxy-client/config.json

    Config for the Galaxy desktop client

    **Example request**:

    .. sourcecode:: http

        GET /desktop-galaxy-client/config.json HTTP/1.1
        Host: cfg.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "status" : "online",
          "channel" : "production",
          "talkInterval" : 600,
          "complainInterval" : 600,
          "timestamp" : 0,
          "end_points" : {
            "files" : "galaxy-client-update.gog.com",
            "products" : "products.gog.com",
            "users" : "users.gog.com",
            "auth" : "auth.gog.com",
            "cdn" : "cdn.gog.com",
            "productsDetails" : "api.gog.com",
            "gameplay" : "gameplay.gog.com",
            "gog-api" : "api.gog.com"
          },
          "intervals" : {
            "quick" : 1,
            "presence" : 5,
            "short" : 10,
            "normal" : 60,
            "selfUpdateCheck" : 360,
            "long" : 1440,
            "eternity" : 10080
          }
        }

.. http:get:: /(str:project)/4/master/(str:os).json

    Returns the file list for the Galaxy Updater

    :param project: Name of the application, possible values:
        desktop-galaxy-client, desktop-galaxy-commservice,
        desktop-galaxy-overlay, desktop-galaxy-peer, desktop-galaxy-updater.
    :type project: str
    :param os: Target OS, possible values: files-windows, files-osx
    :type os: str

    **Example request**:

    .. sourcecode:: http

        GET /desktop-galaxy-peer/4/master/files-windows.json HTTP/1.1
        Host: cfg.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "baseURI": "https://galaxy-client-update.gog.com",
          "files": [
            {
              "hash": "cb1e2b55abc8fac1ce0dd83477a25109",
              "path": "peer/msvc-15/GalaxyPeer.dll",
              "resource": "GalaxyPeer/86194099/windows/peer/msvc-15/GalaxyPeer.dll.zip",
              "size": 2223179
            },
            {
              "hash": "72c2cbd0aff710a34c91596337767675",
              "path": "peer/msvc-15/GalaxyPeer64.dll",
              "resource": "GalaxyPeer/86194099/windows/peer/msvc-15/GalaxyPeer64.dll.zip",
              "size": 3090331
            }
          ],
          "projectName": "GalaxyPeer",
          "symlinks": [],
          "timestamp": "86194099",
          "version": "0.0.0.676"
        }


chat.gog.com
------------

.. http:get:: /users/(int:user_id)/friends

.. http:get:: /users/(int:user_id)/invitations


gameplay.gog.com
----------------

.. http:get:: /clients/(int:product_id)/users/(int:user_id)/achievements

    Gets the achievements list for a product.

    **Example request**:

    .. sourcecode:: http

        GET /clients/1437060567/users/48628349957132247/achievements HTTP/1.1
        Host: gameplay.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "total_count": 40,
          "limit": 1000,
          "page_token": "0",
          "items": [
            {
              "achievement_id": "48497841707623054",
              "achievement_key": "ACHIEVEMENT_NODEATH1",
              "visible": true,
              "name": "Early Bird",
              "description": "Complete level 1 «after a long night» without dying",
              "image_url_unlocked": "https://images.gog.com/296efc79b94a252a68dcd4b3b073b94307930b160603b2083f2dcddb68353c1e_gac_60.jpg",
              "image_url_locked": "https://images.gog.com/3af2d24d7c71bc7a36f69b16c2bdee9daa6fddb285ca2b02c0834e28ee669462_gac_60.jpg",
              "date_unlocked": null
            },
            {
              "achievement_id": "48225958150521213",
              "achievement_key": "ACHIEVE_AVALANCHE",
              "visible": true,
              "name": "Run like hell",
              "description": "Escape the collapsing mine without being crushed",
              "image_url_unlocked": "https://images.gog.com/0c541a40fb04294dfca5b91a659217175bffcce1f13b4c8f875ac562b3c65f8c_gac_60.jpg",
              "image_url_locked": "https://images.gog.com/e53817dce9e0a8f04b180999da9900b238217a9a4c0673d2848bc724c3698921_gac_60.jpg",
              "date_unlocked": null
            }
          ]
        }

.. http:get:: /clients/(int:product_id)/users/(int:user_id)/sessions

.. http:get:: /clients/(int:product_id)/users/(int:user_id)/friends_achievements_unlock_progresses

.. http:get:: /clients/(int:product_id)/users/(int:user_id)/friends_sessions


presence.gog.com
----------------

.. http:post:: /users/(int:user_id)/status

    Pings the server to mark you as online. Keep in mind that the request
    content is a url-encoded form, not JSON.

    :form version: Version of the Galaxy client.

    **Example request**:

    .. sourcecode:: http

        POST /users/48628349957132247/status HTTP/1.1
        Host: presence.gog.com
        Content-Type: application/x-www-form-urlencoded

        version=1.1.22.11

    **Example response**:

    No content


.. http:delete:: /users/(int:user_id)/status

    Marks you as offline.

    **Example request**:

    .. sourcecode:: http

        DELETE /users/48628349957132247/status HTTP/1.1
        Host: presence.gog.com

    **Example response**:

    No content


users.gog.com
-------------

.. http:get:: /users/(int:user_id)

    Returns information about the user

    **Example request**:

    .. sourcecode:: http

        GET /users/48628349957132247 HTTP/1.1
        Host: users.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "id": "48628349957132247",
          "username": "Yepoleb",
          "created_date": "2015-12-04T14:02:42+00:00",
          "avatar": {
            "gog_image_id": "3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d",
            "small": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_avs.jpg",
            "small_2x": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_avs2.jpg",
            "medium": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_avm.jpg",
            "medium_2x": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_avm2.jpg",
            "large": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_avl.jpg",
            "large_2x": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_avl2.jpg",
            "sdk_img_32": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_sdk_img32.jpg",
            "sdk_img_64": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_sdk_img64.jpg",
            "sdk_img_184": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_sdk_img184.jpg"
          },
          "is_employee": false
        }
