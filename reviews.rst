Reviews
=======

.. http:get:: /reviews/product/(int:game_id).json

    Returns the reviews for a game.
    
    :query page: Page number
    
    **Example request**:
    
    .. sourcecode:: http
    
        GET /reviews/product/1207659103.json HTTP/1.1
        Host: embed.gog.com

    **Example response**:
    
    .. sourcecode:: json
    
        {
          "reviews": [
            {
              "id": 12345,
              "title": "Really Good Game",
              "teaser": "Best Point&amp;Click game ever.",
              "description": "Best Point&amp;Click game ever. I like it.",
              "author": {
                "name": "Yepoleb",
                "avatarPath": "https://images.gog.com/3f9e109ac09308f7d52c607c8571e63d5fb482acca499a83e767dfff7f00d57d_avm.jpg",
                "id": "48628349971017"
              },
              "helpfulVotes": 182,
              "totalVotes": 218,
              "rating": 50,
              "added": 1238880457,
              "edited": -62169992008
            }
          ],
          "ts": null,
          "page": 1,
          "totalPages": 19,
          "totalResults": "92"
        }
    

.. http:post:: /reviews/vote/review/(int:review_id).json

    Vote if an individual review is helpful.
    
    :param review_id: ID of the review to be voted on
    :type review_id: int
    
    :reqjson bool wasHelpful: Whether the review was helpful or not
    
    **Example request**:
    
    .. sourcecode:: http
    
        POST /reviews/vote/review/1234567.json HTTP/1.1
        Host: embed.gog.com
        
        {
            "wasHelpful": true
        }
    
    **Example response**:
    
    .. sourcecode:: json
    
        {}

.. http:post:: /reviews/report/review/(int:review_id).json

    Reports a review.
    
    **Example request**:
    
    .. sourcecode:: http
    
        GET /reviews/report/review/10123.json HTTP/1.1
        Host: embed.gog.com
        
        {}
    
    **Example response**:
    
    .. sourcecode:: json

        {
            "reported": true
        }

.. http:post:: /reviews/rate/product/(int:game_id).json

    Submits a game rating.

    :reqjson int rating: Rating in stars * 10

    **Example request**:
    
    .. sourcecode:: http
    
        GET /reviews/rate/product/1436869408.json HTTP/1.1
        Host: embed.gog.com
        
        {
          "rating": 40
        }
    
    **Example response**:
    
    .. sourcecode:: json

        {}

.. http:post:: /reviews/add/product/(int:game_id).json

    Submits a game review.
    
    TODO
