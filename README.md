
# Accouting balance
------------------------------------------------------------------------
We have cash on delivery payments, usually we got payments for it after two weeks after delivery. That means we create invoice in account system when order was shipped and than create payment after 2-3 weeks when we got money for that order. Main issue is invoiced total is not same as payment total because if conversion rates, not 100% precision while shipping calculation and also bank fee. 

Example we have sent COD for 40 USD and got 38.8 USD
Invoice created with 40 USD
Payment should be 38.8 USD

Acceptable solution edit invoice with pro rate sub totals.

----------
**Write function with input parameters from A. and in result should be B.**
 
- A. Order in our CMS:
 1. List of products(Subtotal)
 2. Shipping Price
 3. Discounts (can be applied on order, shipping price, directly on the product)
 4. Total Price = Subtotal + Shipping Price - Discounts

- B. Invoice in accounting system:
 1. List of products(Subtotal)
 2. Shipping Price
 3. Discount (can be applied on subtotal only)
 4. Total Price = Subtotal - Discount + Shipping Price

Total Price paid by customer is received after invoice creation. It's always different from invoice total price.

**Goal:** Create payment for the invoice with correct amount(received from customer) and close the invoice.

**Few rules:**
1. Should be 0 amount A-B
2. You can't edit total in B
3. pro rate in A and B should be same including discount
4. as we can't use discount per shipping (but keep in mind, what our discount could be on subtotal, total or shipping, also could be few discounts) 
so just reduce shipping on discount shipping

**Problems:**
  1. How to apply Discounts on order total and shipping price.
  2. How to change the total price of the invoice to match received amount (edited)