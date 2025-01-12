## Stock Tracking App

# Use Case 1:  View Stock

Track Stock Portfolio

Goal
Allow the user to view their stock database in real-time.

# Actors
Primary Actor: Cashier (end-user)
# Supporting Actors:
Stock Tracking API - Firebase (to fetch real-time data)

# Preconditions
The employee is registered and logged into the application.

# Basic Flow (Main Success Scenario)
 - User Action: User logs into the application.
System Response: System verifies credentials and redirects the user to the dashboard.
 - User Action: User selects the “Stock Overview” option.
System Response:
 - Retrieves the list of stocks in the user’s portfolio.
 - Fetches current prices, gains/losses, and market trends from the stock tracking backend.
 - Displays portfolio performance, including total gains/losses and stock-wise performance in a summary table.
 - User Action:
User views the portfolio details.
Optionally clicks on a stock to view detailed performance metrics (e.g. Total Sales, historical price graph).
# Alternative Flows
 - Flow A: User Has No Loaded Stock

   - System Response: Displays a prompt to add stocks to the portfolio.
   - User Action: User manually adds stocks by searching and selecting from a database.
 - Flow B: Internet Connectivity Issues

   - System Response: Displays an error message, “Unable to fetch real-time data. Please check your internet connection.”
   - User Action: User can view cached portfolio data (if available).

# Use Case 2:  Add/Edit Stock

Track Stock Portfolio

Goal
Allow the user to add their stock to the stock database in real-time.

# Actors
Primary Actor: Cashier (end-user)
# Supporting Actors:
Stock Tracking API - Firebase (to fetch real-time data)

# Preconditions
The employee is registered and logged into the application.

# Basic Flow (Main Success Scenario)
 - User Action: User logs into the application.
System Response: System verifies credentials and redirects the user to the dashboard.
 - User Action: User selects the “Save Stock” option.
System Response:
 - Adds the details of the product.
 - Product details such as price per unit, name and strength.
 
# Alternative Flows
 - Flow A: Insufficient product information entered

   - System Response: Displays validation errors to prompt user to fill required details.
   - User Action: User manually adds product information.
   

# Use case 3: New  Sale 

## **Actors:**
- **Primary Actor:** Stock App
- **Supporting Actor:** Real Time Stock Database

---

## **Goal:**
To record the sale of products and ensure that the system deducts the corresponding stock from the inventory database.

---

## **Preconditions:**
1. The sales system is operational and has access to the inventory database.
2. Products and stock levels are already recorded in the inventory database.

---

## **Postconditions:**
1. The sale is recorded in the system.
2. The inventory database reflects the updated stock levels for the sold products.

---

## **Main Flow:**
1. **Start Sale Process:**
   - The system initiates the sale process when a product is selected by the cashier.

2. **Add Products to Sale:**
   - The cashier selects products and quantities to be sold.

3. **Verify Stock Levels:**
   - The system checks the inventory database to ensure sufficient stock is available.
   - If stock is insufficient, the system displays an error or allows backordering (if supported).

4. **Calculate Total Sale Value:**
   - The system calculates the total value, based on how much the customer has bought.

5. **Confirm Sale:**
   - The system prompts the user to confirm the sale.
   - Once confirmed, the sale is recorded in the sales database.

6. **Update Inventory:**
   - The system deducts the sold quantities from the inventory database.
   - Any changes trigger inventory reordering workflows (if configured).

7. **Generate Sale Record:**
   - The system generates a sale record, storing details like product IDs, quantities, total price, and timestamp.

---

## **Alternative Flows:**
1. **Insufficient Stock:**
   - If stock is insufficient, the system does not allow the sale to proceed or suggests alternatives (e.g., backorder, similar products).

2. **Database Connection Failure:**
   - If the system cannot access the inventory database, it logs the transaction locally and retries updating the inventory when the connection is restored.

3. **Cancelled Sale:**
   - If the sale is cancelled before confirmation, the system discards all temporary sale data.

---

## **Exceptional Flows:**
1. **Incorrect Product Information:**
   - If the product ID or data is incorrect, the system displays an error and requests a correction.

2. **Concurrency Issues:**
   - If multiple sales are processed for the same product, the system uses transactional locking to prevent stock inconsistencies.

---

## **Extensions:**
- **Reorder Trigger:**
  - If stock falls below the reorder level, the system triggers an automatic reorder process.

- **Reporting:**
  - The sale is immediately included in sales reports for analytics purposes.

- **Audit Logs:**
  - The system logs all updates to inventory and sales records for traceability.



# Diagram

![Stocks](ViewDashboard.png?raw=true "View Stock")



