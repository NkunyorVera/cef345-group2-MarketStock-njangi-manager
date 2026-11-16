# MarketStock: user stories and acceptance criteria

One story for every Must and Should functional requirement in `srs.md`, each with at least two Given/When/Then criteria. Each story is meant to become one GitHub issue with the requirement ID in its title.

Roles: **owner** (Mami Ngum), **assistant** (Divine), **user** (either of them).

## Must have

### US-01 Add a product (FR-01)
As the owner, I want to add a product with its prices and quantity, so that it can be sold and its stock followed.

- Given the owner is logged in, when she saves a product "Sugar (1 kg)" with buying price 800, selling price 1 000, quantity 20 and low-stock level 5, then the product appears in the product list with 20 in stock.
- Given the owner is adding a product, when she leaves the selling price empty and saves, then the product is not saved and the message "Enter a selling price" is shown.

### US-02 Edit a product (FR-02)
As the owner, I want to change a product's details and prices, so that the app follows the prices at the stall.

- Given "Sugar (1 kg)" sells at 1 000 XAF, when the owner changes the selling price to 1 100 and saves, then the next sale of that product uses 1 100 XAF.
- Given the assistant is logged in, when he opens a product, then no option to edit the price is shown.

### US-03 Record a sale (FR-05)
As a user, I want to record a sale of one or more products, so that I see the amount to collect without calculating it by hand.

- Given "Sugar (1 kg)" at 1 000 XAF and "Rice (1 kg)" at 700 XAF, when the user enters 2 sugar and 3 rice, then the line totals are 2 000 XAF and 2 100 XAF and the sale total is 4 100 XAF.
- Given a sale with one line, when the user removes that line, then the sale total is 0 XAF and the sale cannot be confirmed.

### US-04 Confirm a sale (FR-06)
As a user, I want the stock to go down when I confirm a sale, so that the stock in the app matches the shelf.

- Given "Sugar (1 kg)" has 20 in stock, when the user confirms a sale of 2, then the stock becomes 18 and a receipt is shown.
- Given a product with 3 in stock, when the user confirms a sale of 3, then the sale is saved and the stock becomes 0.

### US-05 Refuse a sale above the stock (FR-07)
As the owner, I want a sale refused when the quantity is more than the stock, so that we never sell what we do not have.

- Given "Sugar (1 kg)" with 3 in stock, when the assistant records a sale of 5, then the sale is refused with "Only 3 in stock".
- Given the sale was refused, when the assistant changes the quantity to 3 and confirms, then the sale is saved.

### US-06 Log every stock change (FR-08)
As the assistant, I want every stock change saved with the name of the person who made it, so that I am not blamed for stock I did not touch.

- Given the assistant confirms a sale of 2 "Sugar (1 kg)", when the owner opens the stock log, then it shows the date, the time, the assistant's name, the product and a change of -2.
- Given the owner restocks 10 "Sugar (1 kg)", when she opens the stock log, then it shows her name and a change of +10.

### US-07 Log in (FR-13)
As the owner, I want every user to log in with a username and password, so that only my staff use the app.

- Given a user with a correct username and password, when they log in, then the home page opens.
- Given a wrong password, when the user tries to log in, then they stay on the login page and see "Wrong username or password".

## Should have

### US-08 Restock a product (FR-03)
As the owner, I want to record a restock, so that the stock goes up when goods arrive from Douala.

- Given "Sugar (1 kg)" has 4 in stock, when the owner records a restock of 20 from supplier "Ets Fotso" at buying price 820, then the stock becomes 24.
- Given the owner is recording a restock, when she enters a quantity of 0, then the restock is not saved and "Enter a quantity above 0" is shown.

### US-09 See low stock (FR-04)
As the owner, I want a list of products that are running low, so that I order before they finish.

- Given "Sugar (1 kg)" has a low-stock level of 5 and 5 in stock, when the owner opens the low-stock list, then "Sugar (1 kg)" is on it.
- Given "Rice (1 kg)" has a low-stock level of 5 and 6 in stock, when the owner opens the low-stock list, then "Rice (1 kg)" is not on it.

### US-10 See the daily report (FR-09)
As the owner, I want the total sales and profit for a day, so that I know what the stall made without adding up the exercise book.

- Given three sales on 20 November of 4 100, 2 000 and 900 XAF, when the owner opens the report for 20 November, then it shows total sales 7 000 XAF and 3 sales.
- Given no sale was recorded on 21 November, when the owner opens the report for that date, then it shows 0 XAF and 0 sales.

### US-11 Sell on credit (FR-10)
As a user, I want to record a sale on credit against a customer, so that the debt is not forgotten.

- Given a sale of 3 000 XAF, when the user picks "credit" and enters "Ma Bih, 677 00 00 00", then Ma Bih's balance goes up by 3 000 XAF.
- Given the user picks "credit", when no customer name is entered, then the sale is not saved and "Enter the customer's name" is shown.

### US-12 Record a repayment (FR-11)
As a user, I want to record what a customer pays back, so that their balance is always correct.

- Given Ma Bih owes 3 000 XAF, when the user records a repayment of 1 000 XAF, then her balance becomes 2 000 XAF.
- Given Ma Bih owes 2 000 XAF, when the user records a repayment of 5 000 XAF, then it is refused with "Balance is only 2 000 XAF".

### US-13 See who owes money (FR-12)
As the owner, I want to see which customers owe me money, so that I can ask them to pay on market day.

- Given Ma Bih owes 2 000 XAF and Pa Tabi owes 7 500 XAF, when the owner opens the credit book, then Pa Tabi is listed first.
- Given Ma Bih repays her full balance, when the owner opens the credit book, then Ma Bih is no longer on the list.

### US-14 Manage assistant accounts (FR-14)
As the owner, I want to create and deactivate assistant accounts, so that someone who stops working for me can no longer log in.

- Given the owner creates an account "divine", when Divine logs in with it, then he can record sales and cannot change prices.
- Given the owner deactivates "divine", when Divine tries to log in, then he is refused.

## Non-functional requirements as checks

The Must and Should non-functional requirements apply to every story above. They are checked like this:

| ID | Check |
| --- | --- |
| NFR-01 | Time a trained user recording a sale of 3 products. It must take 30 seconds or less. |
| NFR-02 | Load each page with the browser set to 3G. Each must load in under 3 seconds. |
| NFR-03 | Every amount on every page reads like "23 500 XAF", with no decimals. |
| NFR-04 | Logged in as the assistant, no page offers a way to change a price or delete a record. |
| NFR-05 | Every page is usable at 360 px wide with no sideways scrolling. |
| NFR-06 | Look in the database: no password is stored as plain text. |
