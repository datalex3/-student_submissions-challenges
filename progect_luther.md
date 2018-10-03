Project Luther Proposal

Predicting Turo Rental Prices

Alex Bell

Domain:

Turo is a peer-to-peer car sharing website that allow vehicle owners to rent them out their personal vehicles to drivers. It can be thought of as the "AirBNB" of cars. 
Turo has over 4 million registered users and ovr 170,000 vehicle listings. 

Data from the Turo.com website will be scraped and the following variables analyzed for building a regression model.


Variable         | Type       | Description
------------     | ---------- | ------------
reviews | int | number of reviews
rating | float | avg score 1 to 5
trips | int | number of trips by users
class | object | category of 'Turo' class
type | object | car, suv, van etc.
booking | binary | instant booking y or n
delivery | binary | offers delivery y or n
miles incl | int | miles limit of rental
make | object | make of vehicle
model | object | model of vehicle
age | int | vehicle age 
seats | int | no. of seats
category | object | luxury, economy etc.
color | object | 10 color categories
transmission | object | auto/manual/EV
features | object | AWD convertible, etc.

Other continuous data will be accessed from KBB.com

Variable         | Type       | Description
------------     | ---------- | ------------
MPG | float |miles per gallon
Top Speed | float | attainable mph
acceleration | float | time from 0-60mph
sales price | float | vehicle MSRP
horsepower | float | vehicle HP

These datasets will be combined into data frame and regression analysis applied 
with python scikitlearn and statsmodel.




