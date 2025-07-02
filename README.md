
# M-pesa Express Payments on Frappe Cloud

## Overview

The Frappe Cloud M-Pesa Express integration enables seamless payment processing for users in Kenya via M-Pesa. One of the most widely used mobile money platforms in the region. This integration allows partners to receive payments and users to add credits effortlessly through M-Pesa Express.

----------

## 1. Partner Setup

### Eligibility

Only verified **Frappe Partners** can set up M-Pesa Express as a payment method. This means as a partner you need to contact Frappe and they will enable your account to set up M-Pesa Express.  Each partner must have:

-   A registered **Daraja M-Pesa** account.
    
-   A valid **Paybill or Till Number**.
    
-   The appropriate credentials were obtained from Safaricom's Daraja portal.
    
----------

### Steps to Set Up M-Pesa Express

1.  **Navigate to the "Partnership" Section** on your Frappe Cloud dashboard(Only visible to partners).
 ![image (33)](https://github.com/user-attachments/assets/5a6d0b07-6699-44a1-9500-1918e9833e34)
  
    
2.  You will find two last key tabs:
    
    -   **Local Payment Setup**
        
    -   **Partner Payout**
        

----------

### A. Local Payment Setup

This section is divided into two subsections:

#### i. M-Pesa Express Credentials

-   Click the **Edit** button.
    
-   Fill in the following fields:
    
    -   Consumer Key
        
    -   Consumer Secret
        
    -   Initiator Name
        
    -   Pass Key
        
    -   Security Credentials
        
    -   Till Number
        
    -   M-Pesa Setup ID (can be any meaningful name)
   ![image (1)](https://github.com/user-attachments/assets/038f6938-7119-434e-abb9-0320d8d15a48)
   
        
-   Click **Save**.
    

#### ii. Payment Gateway

-   Configure the following details:
    
    -   **Gateway Name** (e.g., "Navari Gateway")
        
    -   **Endpoint URL**: Callback URL of the partner’s site where the invoice is created.
        
    -   **API Key**: From the partner's site.
        
    -   **API Secret**: From the partner's site.
        
    -   **Currency**: Default is KES (Kenyan Shilling).
        
    -   **Taxes**: Specify VAT (e.g., 16% in Kenya).
        
    -   **Print Format**: Must match the format used on the partner's site.
  ![image (34)](https://github.com/user-attachments/assets/5b9ee314-efde-4102-a2e4-a9929b2f9190)
    
        
-   Click **Save**.
    
> ✅ Once these steps are completed, the M-Pesa integration is ready to accept payments.

----------

### B. Partner Payout

This section allows partners to reconcile and submit the collected amounts to Frappe based on a predefined agreement (e.g., monthly or quarterly or depending with amount).

#### Steps to Create a Payout:

1.  Go to **Partner Payout** tab.
    
2.  Click **New Payout**.
    
3.  On the **New Payment Payout** form:
    
    -   Select **Payment Partner** (your organization).
        
    -   Choose the **Payment Gateway**.
        
    -   Enter **Start Date** and **End Date**.
        
    -   Click **Fetch Transactions**(it fetches transactions from the press, a backend doctype called Payment Partner Transactions).
         ![image (35)](https://github.com/user-attachments/assets/1da4814d-429e-4254-a766-78b4cb7dd3ab)

        
5.  The system will display:
    
    -   Distribution
        
    -   Gross Amount
        
    -   Commission (as per your agreement with Frappe)
        
    -   Net Amount (what you owe to Frappe)
        
6.  Click **Submit**.
    

You will be redirected to the **Partner Payout List** where the transaction is logged.

----------

## 2. User Payment Flow

Users with Kenyan-registered sites will see M-Pesa as a payment option by default.

### Steps to Add Credit Using M-Pesa:

1.  Navigate to **Billing > Add Credit > Overview**.
![image (37)](https://github.com/user-attachments/assets/e9fec037-e6e1-41fd-91c0-11a790043657)

    
2.  In the dialog:
    
    -   Choose **M-Pesa** as the payment method.
        
    -   Enter the amount in **USD**.
        
    -   Select **Payment Partner** (e.g., Navari).
        
    -   Provide:
        
        -   **M-Pesa Phone Number**
            
        -   **Tax ID** (mandatory for eTIMS compliance)
   ![image (36)](https://github.com/user-attachments/assets/62deaf03-2199-4ae1-b830-bbcbbfcbea49)
 
            
4.  Tax and total payable amount (including VAT) are auto-calculated.
    
5.  Click **Make Payment via M-Pesa**.
    

> 💡 This will initiate an **STK Push** to your phone. Confirm the payment using your M-Pesa PIN.

After successful payment:

-   An invoice is generated on the **Partner’s site** based on credentials and details setup on the Payment Gateway section.
    
-   The transaction is recorded on **Frappe Cloud**.
    
-   Your credit balance is updated instantly.
    
-   You can download the invoice (branded with both Frappe and the partner’s details) on invoice tab.
  ![Screenshot 2025-06-06 at 11 16 46](https://github.com/user-attachments/assets/42987335-be5d-437e-9b17-621eac659c33)
  

----------

## 3. Exchange Rate API

To convert USD to KES, the system uses the [Fawaz Currency API](https://github.com/fawazahmed0/exchange-api):

`https://cdn.jsdelivr.net/npm/@fawazahmed0/currency-api@latest/v1/currencies` 

This provides up-to-date exchange rates and is publicly accessible via CDN.

----------

### Simple Flow of what happens
![Screenshot 2025-06-06 at 16 32 21](https://github.com/user-attachments/assets/08da3ab4-724d-4aee-8e3b-613add14ef38)

## Summary

With the M-Pesa Express integration, Frappe Partners can offer fast and localized payment options to their Kenyan customers. From setup to payout and invoicing, the entire process is streamlined to support both business operations and compliance.
