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
