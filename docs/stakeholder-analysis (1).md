**Stakeholder Analysis – Use Case 2: Customer Multi-Vendor Order, Checkout and Payment**

1. 

| Stakeholder | Goals | Responsibilities | Dependencies |
| ----- | ----- | ----- | ----- |
| **Customer** | Purchase available products from multiple producers in one checkout, with clear delivery or collection arrangements. | Browse and search for products, select quantities, review the order, amend unavailable items, confirm the purchase and submit or retry payment. | Depends on producers for accurate product availability and fulfilment; the marketplace system for correct prices, stock checks and order confirmation; and the payment service for payment processing. |
| **Producer** | Receive accurate, confirmed orders with at least 48 hours to prepare products, and receive weekly payments with clear financial records. | Maintain accurate product and stock information, review their producer-specific orders, and prepare products for the agreed delivery or collection arrangements. | Depends on customers for purchases; the marketplace system for order details, notifications, inventory updates and accurate settlement records. |
| **Market Owner / Network Operator** | Operate a reliable marketplace, support successful multi-vendor purchases and collect the network’s 5% commission. | Oversee marketplace operations, establish delivery and collection arrangements with producers, and ensure the system correctly splits orders, calculates producer amounts and commission, and maintains transaction records. | Depends on producers for accurate availability and fulfilment; customers for order information and payment; and the payment service for transaction results. |
| **Payment Service Provider** | Process valid payment requests securely and return clear, accurate transaction results. | Process payment requests, return success or declined results and transaction references, and communicate processing errors where possible. A sandbox or simulated service is used for this project. | Depends on the marketplace system for the correct payment amount, order reference and required payment information, and on the customer for valid test payment details or authorisation. |

2. Requirements

| Requirement ID | Functional Requirement | Relevant Stakeholder(s) | Related Business Process | Expected System Behaviour | Priority | Case Study Evidence |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| FR-01 | The system shall allow customers to browse and search for products. | Customer | Product Discovery | Show products and matching search results. | High | The customer browses or searches the marketplace. |
| FR-02 | The system shall allow products from one or more producers in one basket. | Customer | Basket Management | Keep the selected products and quantities in the customer’s basket. | High | Products from one or more producers are added to the basket. |
| FR-03 | The system shall check product availability and requested quantities at checkout. | Customer, Producer, Marketplace Operator | Checkout Validation | Check every selected item against current availability and stock. | High | All selected products must still be available in the requested quantities. |
| FR-04 | The system shall inform the customer about unavailable items or insufficient stock and ask them to amend the order. | Customer | Checkout Validation | Show the stock problem and allow the customer to change the order before continuing. | High | The customer is informed and asked to amend the order. |
| FR-05 | The system shall identify all producers involved in the order. | Producer, Marketplace Operator | Order Management | Identify which producer supplies each selected product. | High | The system identifies the producers involved. |
| FR-06 | The system shall determine the relevant delivery or collection arrangements. | Customer, Producer, Marketplace Operator | Checkout and Fulfilment Planning | Make the relevant arrangements available for customer review. | High | Delivery or collection arrangements are determined before review and confirmation. |
| FR-07 | The system shall allow the customer to review the order and confirm the purchase. | Customer | Checkout Confirmation | Present the order for review and accept the customer’s confirmation. | High | The customer reviews the order and confirms the purchase. |
| FR-08 | The system shall create the overall marketplace order after customer confirmation. | Customer, Marketplace Operator | Order Management | Create the overall order before submitting payment. This is separate from confirming the order after payment succeeds. | High | The system then creates the overall marketplace order. |
| FR-09 | The system shall separate the overall order into producer-specific order elements. | Producer, Marketplace Operator | Order Management | Group each producer’s items into their relevant part of the order. | High | The order is separated into producer-specific elements. |
| FR-10 | The system shall submit payment to an external or simulated payment service. | Customer, Marketplace Operator, Payment Service | Payment Processing | Send a payment request to the selected test service. | High | Payment is submitted to an external or simulated service. |
| FR-11 | The system shall confirm the order when payment succeeds. | Customer, Producer, Marketplace Operator | Order Confirmation | Treat the order as confirmed after receiving a successful payment result. | High | Successful payment leads to order confirmation. |
| FR-12 | The system shall inform the customer when payment is declined. | Customer | Payment Exception Handling | Show that the payment was declined. | High | A customer whose payment is declined must be informed. |
| FR-13  | The system shall allow the customer to retry a declined payment. | Customer, Payment Service | Payment Exception Handling | Give the customer an opportunity to submit payment again. | High | The customer is given an opportunity to retry. |
| FR-14 | The system shall handle temporary payment-service unavailability through an exception or retry path. | Customer, Marketplace Operator, Payment Service | Payment Exception Handling | Follow a defined recovery path instead of simply ending the process. The exact policy needs agreement. | High | Temporary service unavailability must follow an appropriate exception or retry path. |
| FR-15 | The system shall update the relevant inventory quantities after successful payment. | Producer, Marketplace Operator | Inventory Management | Reduce stock by the quantities purchased in the successful order. | High | Appropriate inventory quantities are updated after successful payment. |
| FR-16 | The system shall notify the relevant producers after successful payment. | Producer, Marketplace Operator | Producer Notification | Notify the producers involved in the confirmed order. | High | Relevant producers are notified after successful payment. |
| FR-17 | The system shall calculate the order amount attributable to each producer. | Producer, Marketplace Operator | Order Financial Calculation | Calculate each producer’s amount from their part of the multi-vendor order. Treatment of deductions needs clarification. | High | Case 2 requires an amount attributable to each producer. |
| FR-18 | The system shall calculate the marketplace’s 5% commission. | Marketplace Operator, Producer | Order Financial Calculation | Calculate commission using the stated 5% rate. The calculation base and rounding rules need clarification. | High | Case 2 explicitly states a 5% marketplace commission. |
| FR-19 | The project shall use a sandbox or simulated payment service. | Customer, Marketplace Operator, Payment Service | Payment Processing | Demonstrate payments using a test service, without live payments or real financial data. | High | Case 2 requires sandbox/simulated payments; the wider case study prohibits live payment systems and real financial data. |

3. Dependencies

| Dependency ID | Depender | Dependee | Dependency Type | Dependency Description | Justification from Case 2 |
| ----- | ----- | ----- | ----- | ----- | ----- |
| D-01 | Customer | Marketplace Operator | Resource | Product information for browsing and searching. | The customer browses or searches the marketplace. |
| D-02 | Customer | Marketplace Operator | Goal | An order containing products that are available in the requested quantities. | The system checks availability and quantities at checkout. |
| D-03 | Customer | Marketplace Operator | Resource | Delivery or collection details for the order. | The system determines the relevant arrangements before customer confirmation. |
| D-04 | Marketplace Operator | Customer | Task | Review the order and confirm the purchase. | The customer reviews and confirms before the order is created. |
| D-05 | Marketplace Operator | External/Simulated Payment Service | Task | Process the submitted payment. | Payment is submitted to the simulated service. |
| D-06  | Marketplace Operator | Simulated Payment Service | Resource | Payment result. | The system follows different paths for successful and declined payments. |
| D-07 | Customer | Marketplace Operator| Resource | Information that payment was declined and an opportunity to retry. | The customer must be informed and allowed to retry. |
| D-08 | Producer | Marketplace Operator | Resource | Notification of their part of a confirmed order. | The system splits the order and notifies the relevant producers after successful payment. |
| D-09 | Producer | Marketplace Operator | Goal | Their share of the order amount is calculated correctly. | Case 2 requires an amount attributable to each producer. |
| D-10 | Marketplace Operator | Producer | Resource | Accurate product availability and stock information. | Checkout requires stock information. Producer responsibility for maintaining it comes from the wider case study. |
| D-11 | Customer | Marketplace Operator | Softgoal | A clear and easy checkout experience. | The wider case study asks for seamless checkout and clear supplier and delivery information. This is a quality interpretation, not a measured acceptance rule. |

4. 
