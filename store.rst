Store
=====

TODO

Cart
----

.. http:get:: /cart

.. http:get:: /cart/add/(int:game_id)

    Adds a single item to the cart.

.. http:post:: /cart/add

    Adds multiple items to the cart.

    :reqjson array product_ids: Items to add

.. http:get:: /cart/add/series/(int:series_id)

    Add a series to the cart.

.. http:get:: /cart/remove/(int:game_id)

    Removes an item from the cart.

.. http:get:: /checkout

    Redirects to order page

.. http:get:: /checkout/manual/(int:product_id)

    TODO


Order
-----

.. http:any:: /checkout/order/(int:order_id)/changeCurrency/(str:currency)

.. http:any:: /checkout/order/(int:order_id)/add/(int:game_id)

.. http:post:: /checkout/order/(int:order_id)/remove/(int:game_id)

    Empty request content

.. http:any:: /checkout/order/(int:order_id)/enableStoreCredit

.. http:any:: /checkout/order/(int:order_id)/disableStoreCredit

.. http:any:: /checkout/order/(int:order_id)/setAsGift

.. http:any:: /checkout/order/(int:order_id)/setAsNotGift

.. http:any:: /payment/process/(int:order_id)

.. http:any:: /payment/ping/(int:order_id)

.. http:any:: /order/checkStatus/(int:order_id)

.. http:any:: /account/settings/orders/resend


History
-------

.. http:get:: /account/settings/orders/data

.. http:any:: /account/settings/orders/resend


Wallet
------

.. http:any:: /wallet/recommendedProducts

.. http:post:: /wallet/funds

    Creates an order to add wallet funds.

    :jsonreq int amount: Amount of money to add in cents
    :jsonreq str currency: Currency code

    **Example request**:

    .. sourcecode:: http

        POST /wallet/funds HTTP/1.1
        Host: embed.gog.com

        {
          "amount": 1000,
          "currency": "EUR"
        }

    **Example response**:

    .. sourcecode:: json

        {
          "redirectToUrl": "/checkout/35a99729ca0d"
        }

.. http:get:: /wallet/transactions/(str:currency)/(int:page)

    Gets the wallet transaction history.

    **Example request**:

    .. sourcecode:: http

        GET /wallet/transactions/EUR/1 HTTP/1.1
        Host: embed.gog.com

    **Example response**:

    .. sourcecode:: json

        {
          "list": [
            {
              "orderId": "2E354EEF0EF2",
              "date": 1481166490,
              "name": "Brothers: A Tale of Two Sons - fair price package",
              "negative": false,
              "balanceChange": "0.20",
              "endBalance": {
                "user_id": "48628349971017",
                "currency_code": "EUR",
                "amount": 20,
                "absolute_amount": 20,
                "formattedAbsoluteAmount": "0.20",
                "formattedAmount": "0.20",
                "lastRecharge": null,
                "last_notification_sent": null,
                "expirationDate": null
              },
              "currency": "EUR"
            }
          ],
          "count": 1,
          "pageSize": 30
        }
