# Test Cases – Checkout – SimpleShop

## 1. Feature Overview

**Feature:** Checkout  
**Module/Area:** Cart & Order Processing  
**Related Requirements:** `REQ-CHK-001`, `REQ-CHK-002`, `REQ-CHK-003`  
**Related Risks:** `R3`, `R4` (see `docs/risk-matrix.md`)

### 1.1 Description

Checkout allows a logged-in user to confirm their cart items, enter shipping and payment details, and place an order. It is a **high-risk, high-value** flow.

### 1.2 In Scope

- Checkout with valid cart and address
- Validation errors for missing address fields
- Handling of empty cart at checkout
- Basic confirmation page behaviour

### 1.3 Out of Scope

- Payment gateway integration details (simulated)
- Tax calculation edge cases (simplified for blueprint)
- Detailed invoice format

---

## 2. Test Cases

| ID               | Title                                                 | Preconditions                                                                    | Steps                                                                                                                                                                                                 | Test Data                                       | Expected Result                                                                                                                                                                | Priority | Type       | Automation | Status | Comments |
|------------------|--------------------------------------------------------|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|------------|-----------|--------|----------|
| CHK-TC-001       | Successful checkout with valid data                    | User logged in; cart contains at least one product                               | 1. Go to Cart page<br>2. Click **Proceed to Checkout**<br>3. Fill in valid shipping address<br>4. Fill in valid payment details (simulation)<br>5. Click **Place Order**                             | Valid address & payment details                | Order is created; user sees Order Confirmation page with order ID; cart is cleared                                                                                             | High     | Functional | Yes       | Ready  | Critical business flow |
| CHK-TC-002       | Validation errors for missing mandatory address fields | User logged in; cart contains at least one product                               | 1. Go to Checkout<br>2. Leave required address fields empty (e.g. city, postal code)<br>3. Click **Place Order**                                                                                     | Partial/empty address                          | Appropriate validation messages are shown for each missing field; order is **not** created                                                                                     | High     | Negative   | Yes       | Ready  |          |
| CHK-TC-003       | User cannot checkout with an empty cart                | User logged in; cart is empty                                                    | 1. Navigate directly to Checkout (if URL accessible) or click Checkout with empty cart                                                                                                              | n/a                                             | User is redirected back to an appropriate page (e.g. Cart or Products) with a message indicating that the cart is empty; no order is created                                   | Medium   | Negative   | Yes       | Ready  |          |
| CHK-TC-004       | Order summary matches cart content                     | User logged in; cart has 2–3 items with known prices and quantities              | 1. Go to Checkout<br>2. Verify order summary (item count, unit price, total price)<br>3. Place order                                                                                                | Known products & quantities                    | Order summary shows correct products, quantities, and totals; confirmation page shows same amounts                                                                            | High     | Functional | Yes       | Ready  | Good for API+UI validation |
| CHK-TC-005       | User can see order in order history after checkout     | Successful checkout completed in previous test case                              | 1. Navigate to Profile/Orders page<br>2. Locate the last order<br>3. Verify order details (ID, date, total amount)                                                                                  | Recent order ID from CHK-TC-001                | Order appears in order history with correct data                                                                                                                              | Medium   | Functional | Later     | Draft  | Connects Checkout and Profile features |
