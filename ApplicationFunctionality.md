###Functionality and how it came to be.

We used a combination of JavaFX and SpringBoot to create our hotels booking Management System.
The mapping was completed using Hibernate, and the database was managed through JPA repositories and mySQL.

Our System breaks down into the following layers.
* The user interface that is defined using JXML sheets.
* Our controller Layer which interacts with the User interface.
* The Service layer that handles our business logic to control how actions are performed.
* The Repository that interacts with our database
* The database itself which runs on MySQL.

###Brief Breakdown on each system and why we picked them.

####Why Spring Boot?
The choice for Spring Boot is due to two reasons, one because of its stand-alone application qualities and helps create a perfect foundation for a simple application. The second reason is due to the expertise of our team member.

####What is Hibernate and how does it fit in our framework?
We used Hibernate for our mapping from the tables of our database to our entity classes. It is one of the most popular mapping tools in the industry which is why we are using this specific one to use as a link to our database.

#####Why a mapping tool? 
It is far more user friendly, manual mapping would take too much time to implement. This way we can easily add new objects to be mapped to our tables in our mySQL database, we don’t lose time on that. It is also a way to store persistent data. This to prevent data loss during a black out.

####JavaFX
JavaFX is a open source client platform built for Java, it can produce rich applications and allows for a faster development with modern efficient visual effects being made. Currently on its 11th version it is a well-developed system.
JavaFX uses Fxml forms that are native to JavaFX they are a scriptable and based on the XML markup language. These are used to construct the java object graphs, the hierarchical structure of an XML document closely parallels the structure of a javaFX screen graph.

####JavaFX how does it work?
In order for the graphical user interface to work, the program utilizes JavaFX for example to generate a login screen. The login screen of the hotel application has a username, password field and a login button. It also has a background. With the help of the FXML file, the welcome screen can be changed/customized as deemed necessary. Any utility or functionality can be added to the respective fields/buttons added in the FXML file by using the FXML controller.

####Why MySQL?
MySQL was chosen as MySQL is an open-source relational database management system that works on our platform. It is a common solution to use for a database and there is lots of documentation available that helps with connecting it with the data service layer in our Hotel management system and specifically the spring boot framework.

####Why Gradle over Maven?
Buildtime is a lot faster in Gradle than in Maven, which allows for faster building and user testing. The downside to Gradle is that it is not supported for as long as Maven is, understanding your way around could prove to be slightly more difficult.


####Brief explanation of the logic.
Our program mainly uses services, converters, controllers, repositories, entities and dtos.

The use of Dtos was a choice of reducing calls to the database. Our team could have kept using entities and updated those as we came along. We weren’t exactly sure what we would need from the beginning. Therefore it made more sense to create dtos as the link in between of the entities as the data model could change and dtos are much more simple to change and update than an entity in our framework.

A good example in our code would be the BookingDto and the Booking entity. They contain similar attributes but the BookingDto is also borrowing information from other entities. When we refer to the BookingDto in our application to provide us the information from the database, the BookingDto is also taking information from the room entity. While the Booking entity does not contain this information. This way we can ensure entities are stored similarly and the dtos can be altered as we please.

###How to access each functionality:

<em> 1. As a user, I should be able to start the application and see a welcome screen </em>

* When using an IDE such as IntelliJ, a user can run the program directly by pressing play on the “HotelProjectSpringApplication.java” file.
* Once the build is finished, the login window will open, welcoming the user and prompting them to enter their username and password.
* After the information has been filled out, the user can then press enter and if the credentials are correct the user will be logged in and welcomed by the welcome screen.


<em> 2. As a user, I must be able to set and change my screen name and my password </em>

* When logged in as a user or an administrator.
* On the home screen, on the right hand side there is a hamburger menu in the top corner. When the user clicks on this it expands.
* The dropdown menu has two options, the user clicks the top option “Reset Password” this activates a second window. The window is titled “Reset Password”.
* In the window there are four fields: “Screen Title”, “Current Password”, “New Password” and “Repeat New Password”.
* Changing “Screen Title” changes the displayed text on the home screen - by default for normal users this is set to XXX and for administrators this is set to XXX
* To change the password the user must enter the correct password and two matching new passwords. This is controlled by a logic layer that has restrictions to limit weak passwords.
* Once the user has made the required changes, clicking the “Submit” button sends information to the data access layer to update the database.
* After the update operation has been completed the program shuts down ready for the user to log back in with their new password.


<em> 3. As an administrator, I need to be able to add a room with details (size, beds, number, location and other information)</em>

* When logged in as an administrator.
* JavaFX is used to generate a home screen, this is indicated by the title bar “ADMIN SYSTEM”.
* Clicking the button “Add Room” on the screen activates a second window.
* The second window script has fields in which the administrator can select the size of the room, the number of beds, the location and provide other information in a free text field.
* There is a logic level which performs checks to ensure the room conforms to the set standards and that the creation of the room is possible.
* When the room details are correct, the logic script allows the room to be saved in the database by passing information to the data access layer.

<em> 4. As an administrator, I should be able to change the details of a room </em>

* When logged in as an administrator.
* JavaFX is used to generate a home screen, this is indicated by the title bar “ADMIN SYSTEM”.
* Clicking the button “Room list” on the screen activates a second window.
* On the right hand side of the new window there is a list of all the rooms in the database.
* Details of each room can be displayed by clicking on a row in the list.
* The details of the selected room are displayed on the left in editable fields.
* The fields can be changed by clicking on them, the information is passed to the data access layer by confirming by using the “Update'' button.

<em> 5. As an administrator, I can delete a room </em>

* When logged in as an administrator.
* JavaFX is used to generate a home screen, this is indicated by the title bar “ADMIN SYSTEM”.
* Clicking the button “Room list” on the screen activates a second window.
* On the right hand side of the new window there is a list of all the rooms in the database.
* Clicking on a row, highlights the individual room and shows it is selected.
* To delete from the database the administrator must then click the “Delete” button at the bottom in the center. The information is passed to the data access layer.
* The update to the database is visually confirmed by the removal of the “deleted” row.

<em> 6. As an administrator, I can add a user as either reception staff or administrator</em>

* When logged in as an administrator.
* JavaFX is used to generate a home screen, this is indicated by the title bar “ADMIN SYSTEM”.
* Clicking the button “Add User” on the screen activates a second window.
* In the new window there are four fields: “User Name”, “First Name”, “Last Name”. The last field allows the administrator to choose in the “User Type” field if the new user will be “reception” or “administrator”.
* Logic is used to check if the new user is valid.
* To save the new user to the database, the administrator clicks the “Save” button.
* Currently no indication is presented an action has completed successfully.


<em> 7. As a reception staff, I must be able to see details of a room</em>

* When logged in as reception staff.
* JavaFX is used to generate a home screen, this is indicated by the title bar “User”.
* Clicking the button “Add Booking” on the screen activates a second window.
* In the new window on the left side a details tab for the customer information and booking details tab can be found.
* On the right side of the screen the reception staff can select the type of room by clicking the drop down menu “Room Type” at the top of the window.
* Clicking a room in the “Room Type” menu returns the room details of that selected room.


<em> 8. As a reception staff, I can see all the bookings for a specific day</em>

* When logged in as reception staff.
* JavaFX is used to generate a home screen, this is indicated by the title bar “User”.
* Clicking the button “Booking List” on the screen activates a second window.
* In the new window an oversight of all the bookings will show up.
* On the left-hand side the user can press the drop down menu "Select Filter". The user can then select the filter: "DAY".
* Choosing a date in the DatePicker below it lets you choose a specific day to sort on. Once chosen, pressing the button “Filter” in the bottom left corner refreshes the list to show only the bookings that share the booked date.


<em> 9. As a reception staff, I can see all the bookings for a specific room</em>

* When logged in as reception staff.
* JavaFX is used to generate a home screen, this is indicated by the title bar “User”.
* Clicking the button “Booking List” on the screen activates a second window.
* In the new window an oversight of all the bookings will show up.
* On the left-hand side the user can press the drop down menu "Select Filter". The user can then select the filter: "ROOM".
* Clicking the drop down menu “Select a room” below it lets you choose a specific room to sort on. Once chosen, pressing the button “Filter” in the bottom left corner refreshes the list to show only the bookings with the specified room.


<em> 10. As a reception staff, I must be able to book a room for a specific date range</em>

* When logged in as reception staff.
* JavaFX is used to generate a home screen, this is indicated by the title bar “User”.
* Clicking the button “Add Booking” on the screen activates a second window.
* In the new window on the left side a details tab for the customer information and booking details tab can be found.
* On the booking details tab the reception staff can choose the “From date” and the “To date”, the number of people booking, payment method and the option to include lunch and/or breakfast.
* On the left side of the screen the reception staff can select the type of room by clicking the drop down menu “Room Type”.
* Next to the “Room Type” menu, the reception staff can press the button “Search”.
* When the button “Search” is pressed, logic is used to determine if the date has already been booked. If the room has not been booked the reception staff can then select the room for the given time period and then press the button “Save Booking” in the bottom left corner. The booking is now saved in the system.

<em> 11. As a reception staff, I can see an overview of the bookings</em>

* When logged in as reception staff.
* JavaFX is used to generate a home screen, this is indicated by the title bar “User”.
* Clicking the button “Booking List” on the screen activates a second window.
* In the new window an oversight of all the bookings will show up.

<em> 12. As a reception staff, I will be able to change a booking </em>

This is the only functionality that is missing. This is due to time constraint.

<em> 13. As a reception staff, I can mark a room booking as paid </em>

* When logged in as reception staff.
* JavaFX is used to generate a home screen, this is indicated by the title bar “User”.
* Clicking the button “Booking List” on the screen activates a second window.
* In the new window an oversight of all the bookings will show up.
* In the list, the reception staff can mark a room.
* On the bottom left of the window the button “Marked as Paid” can be pressed.
* The room will now show up as paid in the list.

<em> 14. As a reception staff, I can create a customer with data (name, address, payment method etc) </em>

* When logged in as reception staff.
* JavaFX is used to generate a home screen, this is indicated by the title bar “User”.
* Clicking the button “Add Customer” on the screen activates a second window.
* In the window “Add Customer” the following fields are available: “Name”, “Surname”, “Age”,  “Gender”, “Country”, “City”, “Street” and “Zip-Code”. If filled out, logic is used to determine whether the information is in the correct format.
* After logic tests passed the user can then be added to the database by pressing the button “Save”.


Alternative version 14
* When logged in as reception staff.
* JavaFX is used to generate a home screen, this is indicated by the title bar “User”.
* Clicking the button “Add Booking” on the screen activates a second window.
* In the new window on the left side a details tab for the customer information and booking details tab can be found.
* The customer information tab has the fields: “First Name”, “Last Name”, “Date of Birth”, “Gender”, “Street”, “City”, “Country” and “Zip Code”.
* On the booking details tab the reception staff can choose the from and to date, the number of people booking, payment method and the option to include lunch and/or breakfast.
* On the left side of the screen the reception staff can select the type of room by clicking the drop down menu “Room Type”.
* Next to the “Room Type” menu, the reception staff can press the button “Search”.
* When the button “Search” is pressed, logic is used to determine if the date has already been booked. If the room has not been booked the reception staff can then select the room for the given time period and then press the button “Save Booking” in the bottom left corner. The booking is now saved in the system.


<em> 15. As a reception staff, I can change details for a customer </em>

* When logged in as reception staff.
* JavaFX is used to generate a home screen, this is indicated by the title bar “User”.
* Clicking the button “Customer Details” on the screen activates a second window.
* In the window “Customer List”, on the right-hand side there is a list of customers.
* Clicking on a row in the list brings up the customer information on the right-hand side of the window.
* On the left side the reception staff is free to alter the fields:  “Name”, “Surname”, “Age”,  “Gender”, “Country”, “City”, “Street” and “Zip-Code”. After changing the information the button “Update” is used to save the information to the database.
* Logic is used to determine whether the new information is valid and if so, the save will be successful.
* The reception staff is able to fully remove the user from the database from the same window by pressing the button “Delete Customer” when selecting the desired row in the list. After pressing the button, the customer information is then deleted.


<em> 16. As a reception staff, I must be able to search for a booking</em>

* When logged in as reception staff.
* JavaFX is used to generate a home screen, this is indicated by the title bar “User”.
* Clicking the button “Booking List” on the screen activates a second window.
* In the new window an oversight of all the bookings will show up.
* On the left-hand side the user can press the drop down menu "Select Filter". The user can then select the filter: "CUSTOMER_NAME".
* Typing in the search field "Search for a name” below it lets you write a specific last name to sort on. Once chosen, pressing the button “Filter” in the bottom left corner refreshes the list to show only the bookings with the specified last name.

<em> 17. As a reception staff, I can search for available free dates for rooms</em>

* When logged in as reception staff.
* JavaFX is used to generate a home screen, this is indicated by the title bar “User”.
* Clicking the button “Add Booking” on the screen activates a second window.
* In the new window on the left side a details tab for the customer information and booking details tab can be found.
* On the booking details tab the reception staff can choose the “From date”, and the “To date”, the number of people booking, payment method and the option to include lunch and/or breakfast.
* On the right-hand side of the window the reception staff can select the type of room by clicking the drop down menu “Room Type”.
* Next to the “Room Type” menu, the reception staff can press the button “Search”.
* When the button “Search” is pressed, logic is used to determine if the date has already been booked. If the room has not been booked the reception staff can then select the room for the given time period and then press the button “Save Booking” in the bottom left corner.



Extra information regarding the functionality of the program.
Deleting a customer while they have a booking is not possible, this is because while a booking is active, the booking needs to be deleted first before the system will accept the deletion of the customer.

The team didn't manage to finish 12 to edit/delete a booking. This was due to time constraint. The idea was to add into the Booking List window for changing the booking information per booking. You would be able to search for them, change them, delete them in the same window.
