# Instructions #

The idea of this example project is to gain insight into how you as a developer think about problem solving while demonstrating:
 
 * Application of solid principles
 * A good understanding of separation of concerns without over engineering 
 * Overall approach to unit testing

The test and it's content is not a direct reflection of the work that will be undertaken at Bauer Media but is a technical screen to see how candidates solve problems.

There are no enforced frameworks or tools that *have* to be used. Candidates are free to use whatever feels most comfortable.

## The Brief ##

> You have inherited a legacy restaurant guide application that requires some upgrades to bring it up to date with modern techniques and practices while taking into account separation of concerns, unit testability and the ease of post deployment database tuning and optimisation. Any UI considerations are a value add, but will also be seen in a positive light.


1. Taking the legacy code in `HomeController`, refactor the application into a layered architecture using the `Restaurant` domain model object as a base and the provided `AppData` database as a data store. Use any preferred data access/ORM framework. Scope for demonstrating the following:
  
    * Creation of a Data access layer taking into account web security best practices. Feel free to use any appropriate design patterns you feel comfortable implementing.  
    * The potential definition of a unit testable business logic layer to sit between your controller and your data layer.  
    * The use of dependency injection for better unit testing.  
    * Creating a strongly-typed ViewModel

2.	Implement the `Save` method at `/Restaurant/Edit`. 
  
	* As with task 1, show a layered architecture. Refactor as you see fit.  
	* At a minimum, support editing of the currently shown fields (`Title`, `Phone number`).  
	* The phone number must be validated and stored correctly according to rules listed below. Any client side validation should not interfere with compliance to these rules. Consider unit testing this logic.   
	* The database update **must** be implemented using a stored procedure, but can be abstracted in anyway you see fit.

3.  Optional bonus points for show-offs: Extend the `/Restaurant/Edit` form to include any other fields in a domain specific way, e.g. 
    
    * Cuisine (a dropdown list)  
    * Rating field  
    * Address fields  
    * Latitude/longitude.  
    * Review text in an easy to edit and format way.  
    * Photo upload

## Phone number rules  ##
1. Phone numbers are assumed to be valid within Australia area code - never international
1. Any non-digit characters should be accepted by the UI but ignored/stripped out during parsing. 
1. If less than 9 significant digits are entered, the number is rejected as invalid
1. Any digits beyond the 9th-most-significant are ignored/dropped
1. The resulting 9-digit number must be stored in th `PhoneNumberKey` field
1. The resulting 9-digit number must be formatted as `(00) 0000 0000` before storage in the `PhoneNumberText` field

## Submission ##

When you have completed the task

- Zip the entire solution. 
- Include the `.git` folder so as to include commit history
- Ensure your submission passes the works-on-my-machine test. 
	- Submissions requiring nuget restore are fine (and preferred)
	- Submissions that fail to run due to missing/non relative database paths will be at a disadvantage.
- Return it to the contact you have been given via email/dropbox/s3/etc
- You may not have had time to modify the solution exactly as you would like. If not, include some comments about what other technical debt or architecture you would like to improve upon.