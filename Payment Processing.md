# Payment Processing

## Payment Gateway
The Payment Gateway is responsible for sending the credit card to the appropriate Internet Merchant Account over secure online channels.  The approval or decline of the transaction, however, is actually performed by the Merchant Account.  It is helpful to think of the Gateway as a router that sends the credit card information to the appropriate account.  It is also responsible for fraud checking and maintaining reliable links with the merchants.

There are a number of Payment Gateways, but the major ones include Authorize.net, PayPal (they have a number of products with Website Payments Pro and PayFlow Pro being the main ones), and First Data.  Companies like Authorize.net greatly simplify the process of going online if you have a Merchant Account.  Part of their setup will create the Internet Merchant Account, so you are spared some of the complexity of that step.

## Your Application
Your application can interact with the Payment Gateway in a number of different ways.  For simple applications, such as a shopping cart program, the user may simply be transferred to a web page on the Gateway for credit card processing.  When the transaction is complete, the user is transferred back to the application.  At no point does the application handle the credit card information.

For more sophisticated applications, such as online registration, the program actually controls the entry of the user’s credit card and passes the information to the Gateway through a secure channel called an API (Application Programming Interface). Such programs are called third-party applications and are required to meet high security requirements.  One of these is that the credit card information should be passed to the Gateway and not stored on the application server.

So here is a summary of how the process would work if you had an application such as online registration:

- User enters credit card information into the application
- Credit card information is sent to the Payment Gateway via a secure channel
- The Payment Gateway routes the credit card to the appropriate Internet Merchant Account
- Internet Merchant Account connects to the Merchant Account for credit card processing.
- The result is passed back to the Gateway and then the application.

## Validation, Refunds, and Settlement
If the customer’s credit card is declined you will usually see a general message such as “there was a problem processing your credit card.”  For security reasons, the online user will usually not see the specific reasons for the failure, such as a decline. (The reason for this is that too much information makes it easier for hackers to fake credit card transactions.) However, the management side of the Gateway and third-party applications may allow you to find out more specific reasons for the failure.

If the card is cleared, the Gateway will return one or two order numbers that are used for future reference of the transaction.  These order numbers are used so that the credit card information does not need to be stored on the Gateway or third-party application.  A common use of the order number is for credit card refunds.  Refunding via a reference to transaction is much safer than refunding directly to the card. For example, you would not be able to refund more than the amount of the original transaction.

Once the card clears, the money will not appear immediately in your bank.  Settlement refers to the process of transferring funds from the buyer to your bank.  This process – managed by the Merchant Account – usually takes several business days.  Before Settlement occurs, you will usually have time to void the original transaction if there was a mistake.

## Fees!
Although we’ve worked through the key concepts of online credit card processing, we still have one last area of confusion, which are fees.  Admittedly, the number of fees can be quite confusing, but the general formula is usually straight forward.

- The Merchant Account will have one or more of these fees:
- One-time setup fee
- Recurring monthly fees
- Per Transaction fees.  While there may be a fixed transaction fee (usually 25 cents or less), the most important fee is the Percentage Fee, which will typically range from 2.00-3.00% for MasterCard/Visa and 4.00-5.00% for American Express.  If you do any reasonable level of volume, the Percentage Fees will dwarf all the other fees discussed in this section.  Consequently, the discussions you have with your Merchant Account administrator will be the most important you’ll have in terms of managing the total amount of your fees.
- The Payment Gateway and, possibly, the Internet Merchant account will have this structure:
- One-time setup fee (typically in the $100-200 range)
- Recurring Monthly Fee (typically in the $20-60 range)
- Per Transaction fee.  Some gateways waive this fee in favor of a higher monthly transaction fee.  Otherwise, this fee is relatively low on the order of 25 cents.  If you have large volume (3,000 or more transactions per month, for example), you may be better off paying a higher monthly fee instead of per transaction charges.
Setting up online credit card processing may require a lot of up front work and assistance, but once you are on the air you will see huge benefits in terms of work automation, increased revenue streams, and improved cash flow.