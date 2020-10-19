PayPal payments can be created and associated with an order in a few steps:

1. Create a Paypal payment, passing a valid `return_url` and `cancel_url`
2. Get the `approval_url` from the response
3. Redirect the customer to the approval URL
4. Get the `paypal_payer_id` from the return url parameters
5. Update the PayPal payment with the payer ID

PayPal payments are one-time payment sources and cannot be saved in customer wallets.
