# Farmacy foods - architecture kata

The png file represents a high level architecture for the farmacy foods systems. 
Here's a basic information on how to interpret the diagram. 
- The dotted lines represents communication with the queues. 
- The solid lines represent restful communication 
- the dark blue lines represent that communication with end user.
- The grey boxes represent a deployable service
- The rounded boxes represent a module or functionality that is required by the application.
- The stick figures are different user roles.

## Assumptions:

### User roles
**Customer** : 
 - should be able to book a meal subscription from the available menu of the kitchen
    - should be able to get notified of the meal delivery and tracking
    - should be able to pay for the meal subscription
    - should be able to apply coupons
 - should be able to browse what meal is available in a given smart fridge, kiosk around them based on location
 - should be able to pay for the meal at POS 
   - should be able to apply coupons
 - should be able to authenticate themself 

**kitchen admin** : Every sale front is associated to a kitchen, depending on the geography
 - has the ability to add a fridge to the kitchen
 - should be able to read/update the kitchen's menu
 - should be able to read/update the availability of items in the kitchen for subscription
 - should be able to set the pricing of items
 - should be able to release discount coupons
 
**sale front operators** : sale fronts are smart fridges, kiosks
 - should be able to add/remove items from the fridge
 - should be able to accept payments for meal
 - should be able to dispense meals from fridge
 - should be able to authenticate themself

**central admin** : the root user
- should be able to add fridge operators, kitchen admin
- should be able to create/remove another central admin
- do everything that a kitchen admin or sale front operator can do.

**delivery agent** : Updates shipment delivery status
- should be able to update shipment delivery status
- should be notified of new delivery task.


### General Assumptions:
- We are assuming that a every type of user can access the application with a mobile and web frontend, which already exists or is being developed parallely. Therefore the architecture of the front end systems is outside the scope of this for now.

### service responsibilities
**People management**
  - manages the various user types of the system like customers, operators, etc.

**Sale front**
  - A sale front represents the point of sale. It could be a smart fridge or a kiosk. The sale front service talks to these point of sale systems and manages data in them. For example, an operator can talk to sale front service to update the inventory after restocking. Also every sale transaction will be captured and published to the transactions queue to update the inventory status.
  
**Product management**
  - This service handles creation and updation of product catalogue. It also helps the kitchen admin or kitchen manager to know the status of the inventory that he/she is managing. They can also update the kitchen menu.
  - Talks to inventory tracker to list only the available items.

**Authentication and authorization**
  - Handles authentication and authorization.

**Order management**
  - Handles all the orders arriving on the system as well as the feedback for the orders. At the moment they are the subscription orders. Uses RDBMS so that we have better support for transactions if the need be.

**Inventory tracker**
  - Handles the inventory management. Picks up the transaction details from the transaction queue to update the inventory status. It also notifies the product management about items going out of stock.

**Shipping**
  - tracks status of various shipments like shipments for customers and also for restocking

**Payments**
  - Is a third party system being used currently.

**location service**
  - Is a third party location service to search for the sale fronts nearby

**Accounting**
  - Is a third party service.


