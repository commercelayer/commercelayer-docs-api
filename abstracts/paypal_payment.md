PayPal payments can be created and associated with an order in a few steps:

1. Create a Paypal payment, passing a valid return url and cancel url
2. Get the approval url from the response
3. Redirect the customer to the approval url
4. Get the Payer ID from the return url parameters
5. Update the Paypal payment with the Payer ID

PayPal payments are one-time payment sources and cannot be saved in customer wallets.
