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

.. http:get:: /products

    Same as :http:get:`/products/(int:product_id)`, but supports multiple
    products per request. Results are returned as an array.

    :query str ids: Up to 50 comma separated product IDs.

    **Example request**:

    .. sourcecode:: http

        GET products?ids=1444036272%2C1444035366 HTTP/1.1
        Host: api.gog.com

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

    Returns the list of friends.

    **Example request**:

    .. sourcecode:: http

        GET /users/48628349957132247/friends HTTP/1.1
        Host: chat.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "items": [
            {
              "user_id": "46988961654682898",
              "username": "adaliabooks",
              "is_employee": false,
              "images": {
                "medium": "https://images.gog.com/fc8ebd082c233822f091875ad36c1102a4a7d58be19b73e72c997de681aa40f1_avm.jpg",
                "medium_2x": "https://images.gog.com/fc8ebd082c233822f091875ad36c1102a4a7d58be19b73e72c997de681aa40f1_avm2.jpg"
              }
            },
            {
              "user_id": "47510856674996320",
              "username": "vidsgame",
              "is_employee": false,
              "images": {
                "medium": "https://images.gog.com/4c208a9ee4766deaafce3189ab5c3afea54e85332efed1b3c563dc9954d70a8f_avm.jpg",
                "medium_2x": "https://images.gog.com/4c208a9ee4766deaafce3189ab5c3afea54e85332efed1b3c563dc9954d70a8f_avm2.jpg"
              }
            }
          ]
        }

.. http:get:: /users/(int:user_id)/invitations


content-system.gog.com
----------------------

.. http:get:: /products/(int:product_id)/os/(str:os)/builds?generation=2

    Returns the available builds for a game.

    :param os: Game OS. Possible values: windows, osx.
    :type os: str
    :query int generation: Max manifest version. Can be 1 or 2.

    **Example request**:

    .. sourcecode:: http

        GET /products/1207658930/os/windows/builds?generation=2 HTTP/1.1
        Host: content-system.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "total_count": 2,
          "count": 2,
          "items": [
            {
              "build_id": "48906206523382029",
              "product_id": "1207658930",
              "os": "windows",
              "branch": null,
              "version_name": "3.5.0.26",
              "tags": [],
              "public": true,
              "date_published": "2016-03-09T10:16:11+0000",
              "generation": 2,
              "link": "https://cdn.gog.com/content-system/v2/meta/92/ab/92ab42631ff4742b309bb62c175e6306"
            },
            {
              "build_id": "3161",
              "product_id": "1207658930",
              "os": "windows",
              "branch": null,
              "version_name": "",
              "tags": [],
              "public": true,
              "date_published": "2015-05-12T09:21:36+0000",
              "generation": 1,
              "link": "https://cdn.gog.com/content-system/v1/manifests/1207658930/windows/37794096/repository.json",
              "legacy_build_id": 37794096
            }
          ],
          "has_private_branches": false
        }


cdn.gog.com
-----------

.. http:get:: /content-system/v1/manifests/(int:product_id)/(str:os)/(int:build_id)/repository.json

    TODO

    **Example request**:

    .. sourcecode:: http

        GET /content-system/v1/manifests/1207658930/windows/37794096/repository.json HTTP/1.1
        Host: cdn.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "product": {
            "timestamp": 37794096,
            "depots": [
              {
                "languages": [
                  "Neutral"
                ],
                "size": "1255672",
                "gameIDs": [
                  "1207658930"
                ],
                "systems": [
                  "Windows"
                ],
                "manifest": "a0e35d92-2a0f-40db-8a47-47cbbad0bac0.json"
              },
              {
                "languages": [
                  "English"
                ],
                "size": "24450928280",
                "gameIDs": [
                  "1207658930"
                ],
                "systems": [
                  "Windows"
                ],
                "manifest": "463cd4b2-783e-447a-b17e-a68d601911e3.json"
              },
              {
                "redist": "MSVC2010",
                "executable": "__redist/MSVC2010/vcredist_x86.exe",
                "argument": "/q",
                "size": "0"
              },
              {
                "redist": "dotNet4",
                "executable": "__redist/dotNet4/dotNetFx40_Full_x86_x64.exe",
                "argument": "/q /norestart",
                "size": "0"
              },
              {
                "redist": "DirectX",
                "executable": "__redist/DirectX/DXSETUP.exe",
                "argument": "/silent",
                "size": "0"
              }
            ],
            "support_commands": [
              {
                "languages": [
                  "Neutral"
                ],
                "executable": "/galaxy_the_witcher2_ee_3.5.0.26.exe",
                "gameID": "1207658930",
                "systems": [
                  "Windows"
                ],
                "argument": ""
              }
            ],
            "installDirectory": "The Witcher 2",
            "rootGameID": "1207658930",
            "gameIDs": [
              {
                "dependencies": [],
                "gameID": "1207658930",
                "name": {
                  "en": "The Witcher 2 - Assassins of Kings Enhanced Edition"
                },
                "standalone": true
              }
            ],
            "projectName": "The Witcher 2 - Assassins of Kings Enhanced Edition"
          },
          "version": 1
        }

.. http:get:: /content-system/v1/manifests/(int:product_id)/(str:os)/(int:build_id)/(str:manifest_id).json

    **Example request**:

    .. sourcecode:: http

        GET /content-system/v1/manifests/1207658930/windows/37794096/463cd4b2-783e-447a-b17e-a68d601911e3.json HTTP/1.1
        Host: cdn.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "version": 1,
          "depot": {
            "name": "The Witcher 2 - Assassins of Kings Enhanced Edition",
            "files": [
              {
                "url": "1207658930/main.bin",
                "size": 128,
                "hash": "4d1daf474729e889b878b9bdef634f76",
                "path": "/CookedPC/dlc_finishers.dzip",
                "offset": 13944149457
              },
              {
                "url": "1207658930/main.bin",
                "size": 262,
                "hash": "3d1be6f328329f983075c124a00aca56",
                "path": "/Launcher/Neutral/textbox_thumb_normal.PNG",
                "offset": 24440333403
              },
              {
                "url": "1207658930/main.bin",
                "size": 417,
                "hash": "1ebd6e11f384c2d10c936155afbcfa13",
                "path": "/Launcher/Neutral/textbox_arrow_pressed.PNG",
                "offset": 24439929797
              }
            ]
          }
        }

.. http:get:: /content-system/v1/depots/(int:product_id)/windows/(int:depot_id)/(str:file)

    **Example request**:

    .. sourcecode:: http

        GET /content-system/v1/depots/1207658930/windows/main.bin HTTP/1.1
        Host: cdn.gog.com

.. http:get:: /content-system/v2/meta/(str:hash)

    Content-System V2 responses are zlib encoded (window size 15).

    **Example request**:

    .. sourcecode:: http

        GET /content-system/v2/meta/92/ab/92ab42631ff4742b309bb62c175e6306 HTTP/1.1
        Host: cdn.gog.com

    **Example repository response**:

    .. sourcecode:: json

        {
          "baseProductId": "1207658930",
          "dependencies": [
            "MSVC2010",
            "MSVC2010_x64",
            "DirectX",
            "dotNet4"
          ],
          "depots": [
            {
              "languages": [
                "*",
                "en"
              ],
              "manifest": "79a1f5fd67f6d0cda22c51f1bd706b31",
              "productId": "1207658930",
              "size": 492
            },
            {
              "languages": [
                "en"
              ],
              "manifest": "32eee2cc5e7da11f22de078eac90ba60",
              "productId": "1207658930",
              "size": 24452205574
            }
          ],
          "installDirectory": "The Witcher 2",
          "offlineDepot": {
            "languages": [
              "*"
            ],
            "manifest": "d1e0f516a5ca1eae591c5969c5044f0f",
            "productId": "1207658930",
            "size": 3046
          },
          "platform": "windows",
          "products": [
            {
              "name": "The Witcher 2 - Assassins of Kings Enhanced Edition",
              "productId": "1207658930",
              "script": "goggame-1207658930.script",
              "temp_arguments": "",
              "temp_executable": "galaxy_the_witcher2_ee_3.5.0.26.exe"
            }
          ],
          "version": 2
        }

    **Example depot response**:

    .. sourcecode:: json

        {
          "depot": {
            "items": [
              {
                "chunks": [
                  {
                    "compressedMd5": "2e0dc2f5707ec0d88d570240ba918bb2",
                    "compressedSize": 9507293,
                    "md5": "b013bcdcb851922f7e3357fd7b1828ed",
                    "size": 10485760
                  },
                  {
                    "compressedMd5": "a7e5eff7ef78707d2d059c724fa3dc8f",
                    "compressedSize": 9617323,
                    "md5": "2b49c180539c7e188cd58e99b1b13f2d",
                    "size": 10485760
                  },
                  {
                    "compressedMd5": "a47d292fc498f740677e640146ad2097",
                    "compressedSize": 14655939,
                    "md5": "c0a2bcb478957dd77d4eec9240f22d4f",
                    "size": 18954814
                  }
                ],
                "md5": "7da354ae24cee72ee8ef64c42944f530",
                "path": "CookedPC\\pack0.dzip",
                "type": "DepotFile"
              },
              {
                "chunks": [
                  {
                    "compressedMd5": "f149b52a4ce1d025bbae57e8f8f7f662",
                    "compressedSize": 351,
                    "md5": "53318eac2bcdac67c84dfde40e58006d",
                    "size": 1024
                  }
                ],
                "flags": [
                  "hidden"
                ],
                "path": "goggame-1207658930.info",
                "type": "DepotFile"
              },
              {
                "chunks": [
                  {
                    "compressedMd5": "0812e871154b26f4737364abc193e2bc",
                    "compressedSize": 1177139,
                    "md5": "143e880fed5ba39967f23785c3cc868b",
                    "size": 1288912
                  }
                ],
                "flags": [
                  "support",
                  "executable"
                ],
                "path": "galaxy_the_witcher2_ee_3.5.0.26.exe",
                "type": "DepotFile"
              }
            ]
          },
          "version": 2
        }


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

    Pings the server to mark you as online. Should be refreshed every 5
    minutes. Keep in mind that the request content is a url-encoded form, not
    JSON.

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

.. http:options:: /statuses

    No idea what this does, but the official client uses it every time before
    doing the GET request. Reponse never contains any items.

    :query str user_id: Comma separated list of user IDs to check the
        status of.

    **Example request**:

    .. sourcecode:: http

        OPTIONS /statuses?user_id=46988961654682898,46988886297334688,47510856674996320 HTTP/1.1
        Host: presence.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "items": [],
          "limit": 250,
          "total_count": 0
        }

.. http:get:: /statuses

    Returns the users who are online at the moment.

    :query str user_id: Comma separated list of user IDs to check the
        status of.

    **Example request**:

    .. sourcecode:: http

        GET /statuses?user_id=46988961654682898,46988886297334688,47510856674996320 HTTP/1.1
        Host: presence.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "total_count": 2,
          "limit": 250,
          "items": [
            {
              "data": {},
              "client_id": "46755278331571209",
              "user_id": "46988961654682898"
            },
            {
              "data": {},
              "client_id": "46755278331571209",
              "user_id": "46988886297334688"
            }
          ]
        }


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
