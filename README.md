# Monthly Budgets

You have two accounts, a credit card and a checking account.  You download your statements every month, and now you
want to generate a report that shows you how much you made per month vs how much you spent.  The catch is that you
don't always make credit card payments in the same month that you purchased the items, so you want to take that into
account.

Your credit card statements look like this:

Description       | Amount       | Date
----------------- | ------------ | ----------
Some product      | $10.00       | 2014-02-04
Payment Thank You | $-100.00     | 2014-02-05

* All amounts are in the same column
* Payments are shown as negative amounts, with the description "Payment Thank You"
* When you purchase things with the card, they appear as positive amounts
* These are CSV files

Your checking account statements look like this:

Description       | Credit      | Debit   | Date
----------------- | ----------- | ------- | ----------
Check #34         |             | $15.00  | 2014-02-03
Deposit ATM       | $4,000.00   |         | 2014-02-04
Payment CC        |             | $100.00 | 2014-02-05

* All amounts are positive
* Credit and Debit are separated into separate columns
* Debit means money left your account
* Credit means you deposited money
* Deposit descriptions may vary
* Credit card payments have the description "Payment CC"
* These are CSV files

Your mission, should you choose to accept it, is to write code to determine your true month-to-month balance,
using the following formula:

    Deposits - (Non-credit-card Withdrawals + Credit Card Purchases)

## Examples

Let's say you have the following data in a given month:

**Credit Card**

Description       | Amount       | Date
----------------- | ------------ | ----------
Some product      | $10.00       | 2014-02-04
Other product     | $5.00        | 2014-02-04
Payment Thank You | $-100.00     | 2014-02-05

**Checking Account**

Description       | Credit     | Debit    | Date
----------------- | ---------- | -------- | ----------
Check #34         |            | $20.00   | 2014-02-03
Deposit ATM       | $100.00    |          | 2014-02-04
Payment CC        |            | $100.00  | 2014-02-05

Your monthly balance for the month would be $65.00 because:

```
Deposits - (Non-credit-card Withdrawals + Credit Card Purchases)
100.00 - (Non-credit-card Withdrawals + Credit Card Purchases)
100.00 - (20.00 + Credit Card Purchases)
100.00 - (20.00 + 15.00)
65.00
```

## Code

Your code should eventually be able to:

* take a directory name
* read all statements in that directory
* do the math
* return an array of months and balances

How you get there is, of course, up to you :)

Consider using the [Money Gem](https://github.com/RubyMoney/money) so you don't end up with floating point math errors.

## Checking your work

Parse all of files in the data directory.  You should get the following balances:

Year | Month         | Balance
---- | ------------- | --------
2014 | January       | $374.94
2014 | February      | $30.79
2014 | March         | $-106.04
2014 | April         | $292.38
2014 | May           | $-37.62
2014 | June          | $-71.33
