Customer passwords can be reset in three steps:

1. Create a new customer password reset with the email of the customer.
2. Get the reset password token from the response.
3. Update the customer password reset resource passing the token and the new password.

It's your responsibility to verify the customer's identity before the third step. A typical flow is to send an email to the customer with a verification link that includes the reset password token.
