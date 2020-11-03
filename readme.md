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


### General Assumptions:
- We are assuming that a every type of user can access the application with a mobile and web frontend, which already exists or is being developed parallely. Therefore the architecture of the front end systems is outside the scope of this for now.
- 