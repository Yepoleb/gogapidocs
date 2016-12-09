Searching
=========

Methods used for searching games.

.. http:get:: /games/ajax/filtered

    Searches for **all available** games matching the given criterias.

    :query category: Game genre
    :query devpub: Developer or publisher
    :query feature: Game features
    :query language: Language
    :query mediaType: Game or movie
    :query page: Page number
    :query price: Price range
    :query release: Release timeframe
    :query search: Search string
    :query sort: Sort order
    :query system: OS
    :query limit: Max results

    **Example request**:

    .. sourcecode:: http

        GET /games/ajax/filtered?mediaType=game&search=Witcher HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "products": [
            {
              "customAttributes": [],
              "price": {
                "amount": "29.99",
                "baseAmount": "29.99",
                "finalAmount": "29.99",
                "isDiscounted": false,
                "discountPercentage": 0,
                "discountDifference": "0.00",
                "symbol": "€",
                "isFree": false,
                "discount": 0,
                "isBonusStoreCreditIncluded": false,
                "bonusStoreCreditAmount": "0.00"
              },
              "isDiscounted": false,
              "isInDevelopment": false,
              "id": 1207664663,
              "releaseDate": 1431982800,
              "availability": {
                "isAvailable": true,
                "isAvailableInAccount": true
              },
              "salesVisibility": {
                "isActive": true,
                "fromObject": {
                  "date": "2015-05-19 02:00:00.000000",
                  "timezone_type": 3,
                  "timezone": "Europe/Nicosia"
                },
                "from": 1431990000,
                "toObject": {
                  "date": "2020-12-31 23:59:59.000000",
                  "timezone_type": 3,
                  "timezone": "Europe/Nicosia"
                },
                "to": 1609451999
              },
              "buyable": true,
              "title": "Witcher 3: Wild Hunt, The ",
              "image": "//images-3.gog.com/60c724a052275a049d857d53957dc38e9347742f52372bb956d992b43efa8fb5",
              "url": "/game/the_witcher_3_wild_hunt",
              "supportUrl": "/support/the_witcher_3_wild_hunt",
              "forumUrl": "/forum/general",
              "worksOn": {
                "Windows": true,
                "Mac": false,
                "Linux": false
              },
              "category": "Role-playing",
              "originalCategory": "Role-playing",
              "rating": 49,
              "type": 2,
              "isComingSoon": false,
              "isPriceVisible": true,
              "isMovie": false,
              "isGame": true,
              "slug": "the_witcher_3_wild_hunt"
            }
          ],
          "ts": null,
          "page": "1",
          "totalPages": 1,
          "totalResults": "1",
          "totalGamesFound": 1,
          "totalMoviesFound": 0
        }

.. http:get:: /account/getFilteredProducts

    Searches for games **owned by the user** matching the given criterias.

    :query category: Genre
    :query feature: Feature
    :query hiddenFlag: Show hidden games
    :query language: Language
    :query mediaType: Game or movie
    :query page: Page number
    :query search: Search string
    :query sortBy: Sort order
    :query system: OS
    :query tags: Tags
    :query totalPages: Total Pages

    **Example request**:

    .. sourcecode:: http

        GET /account/getFilteredProducts?mediaType=1&search=Shadowrun HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "sortBy": "date_purchased",
          "page": 1,
          "totalProducts": 1,
          "totalPages": 1,
          "productsPerPage": 100,
          "contentSystemCompatibility": null,
          "moviesCount": 1,
          "tags": [
            {
              "id": "243982903",
              "name": "COMPLETED",
              "productCount": "0"
            },
            {
              "id": "243982893",
              "name": "NEXT TO PLAY",
              "productCount": "0"
            },
            {
              "id": "243982883",
              "name": "BACKLOG",
              "productCount": "0"
            },
            {
              "id": "243982873",
              "name": "FAVORITE",
              "productCount": "0"
            }
          ],
          "products": [
            {
              "isGalaxyCompatible": true,
              "tags": [],
              "id": 1207660413,
              "availability": {
                "isAvailable": true,
                "isAvailableInAccount": true
              },
              "title": "Shadowrun Returns",
              "image": "//images-2.gog.com/6c35ecb988f57725cc0f385acf860241082da16eda9fab66115f4da883dae3d1",
              "url": "/game/shadowrun_returns",
              "worksOn": {
                "Windows": true,
                "Mac": true,
                "Linux": true
              },
              "category": "Role-playing",
              "rating": 41,
              "isComingSoon": false,
              "isMovie": false,
              "isGame": true,
              "slug": "shadowrun_returns",
              "updates": 0,
              "isNew": false,
              "dlcCount": 0,
              "releaseDate": {
                "date": "2013-07-25 00:00:00.000000",
                "timezone_type": 3,
                "timezone": "Europe/Nicosia"
              },
              "isBaseProductMissing": false,
              "isHidingDisabled": false,
              "isInDevelopment": false,
              "isHidden": false
            }
          ],
          "updatedProductsCount": 0,
          "hiddenUpdatedProductsCount": 0,
          "appliedFilters": {
            "tags": null
          },
          "hasHiddenProducts": false
        }
