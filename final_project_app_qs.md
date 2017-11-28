# SI 364 - Final Project questions

## Overall

* **What's a one-two sentence description of what your app will do?**

  I really want to create an app that can be a more in-depth tool people who are not as familiar with investing can use as a good starting point by taking information like income and using a nice sized well of information about different available stocks from a database to give well rounded advice, then emailing this information to the user . I recognize that this was a concept I used for the midterm, but I feel that the final could be a great opportunity for me to work on this concept and really make it special!

## The Data

* **What data will your app use? From where will you get it? (e.g. scraping a site? what site? -- careful not to run it too much. An API? Which API?)**

	--My app would use market data from the quandl api and a database used to store information on businesses, as well as users so that the data can be used later to update users when more businesses are available for investment suggestions.
	--Possibly a list of state incomes

* **What data will a user need to enter into a form?** 

	-- First Form Login Form:
		A user will need to enter a name and password
	--Second Form Create an account:
		A user will need to enter name, password, and email
	--Third Form Request Suggestion:
		State or Income, Business Ticker symbol(optional), update database request, email request 

* **How many fields will your form have? What's an example of some data user might enter into it?**
Likely 9 Total Fields over the three WTForms
	-- First Form Login Form:
		A user will need to enter a name and password(both StringField)
	--Second Form Create an account:
		A user will need to enter name, password, and email(all StringFields)
	--Third Form Request Suggestion:
		State or Income(DropDownList or IntegerField), Business Ticker symbol(optional and String Field), update database request(Radio field) , email request (Radio Field)

* **After a user enters data into the form, what happens? Does that data help a user search for more data? Does that data get saved in a database? Does that determine what already-saved data the user should see?**

	After the user enters data in the form the users info will be saved in the database and will determine what data thats already saved will be shown, what data will be fetched from quandl and if selected emailed later.

* **What models will you have in your application?**
	--So far I plan on having a User Model, Suggestion Model and Business Model Suggestions

* **What fields will each model have?**
	--Business_Stock_Info class (Representing Business info for suggestion)
  		__tablename__="Businesses"
  		business_name
  		stock_info
  		date_updated

	--User
		id
		name
		email
		password(added depending on how I do user login set up)

	--Suggestions(suggestion information as well as what user its associated with )
		id
		suggestionName
		Businesses= db.relationship
		user_id

	Association table between Businesses and Suggestions 

* **What uniqueness constraints will there be on each table? (e.g. can't add a song with the same title as an existing song)**

--Businesses
	business name and id will be unique
	can't add a business that's already in database
--User
	id name and email will be unique
	(plan on adding a user login setup and then people won't be able to add a user that already exist)
--Suggestions
	id and SuggestionName will be unique
	can't add a Suggestion that already exists


* **What relationships will exist between the tables? What's a 1:many relationship between? What about a many:many relationship?**

	one to many between user and suggestion table as a single user can have many suggestions

	many to many between businesses and suggestion table as a suggestions can be matched with many businesses

* **How many get_or_create functions will you need? In what order will you invoke them? Which one will need to invoke at least one of the others?**

	I plan on making 3 get or create functions one for user, business, and suggestions.

	Invoking user first(should be a part of user login page or create a user page) which will lead to user homepage 

	Will Invoke suggestions then businesses get or create upon Third form submission.

## The Pages

* **How many pages (routes) will your application have?**
	Ten total pages as of now:
	1.Login Page (new)
	2.Page to create a new login(new)
	3.User Homepage(Plan to update so it's better than midterm homepage and relevant for final project)
	4.Form(new/updated for final project)
	5.Result Page(updated)
	6.Show available Businesses(new)
	7.Show User's suggestions(new)
	8.Extra Resources(plan to updated)
	9.500 Error Message for when a entered company doesn't exist
	10.404 Error Message
	

* **How many different views will a user be able to see, NOT counting errors?**

	--Plan on having 8 different view functions that will be viewable by users

* **Basically, what will a user see on each page / at each route? Will it change depending on something else -- e.g. they see a form if they haven't submitted anything, but they see a list of things if they have?**

	--As of now going to the login page will show a form to log in or a link to create an account,if they click the link then they'll get directed to the create an account page, otherwise directs to the user's homepage. From there the user will be able to access the wtf form to get investment suggestions, go to either available businesses/all of users suggestions pages or Extra resources page.  

## Extras

* **Why might your application send email?**
	--Would send email to user to notify when database has been updated or email the suggestions

* **If you plan to have user accounts, what information will be specific to a user account? What can you only see if you're logged in? What will you see if you're not logged in -- anything?**

	--User can only see user's previous suggestions and access the site(includes wtf form to get suggestions(may change this)) if logged in(may alter access to form as well as notification options)

* **What are your biggest concerns about the process of building this application?**
	--I think the set up off the app should be do able and awesome for the final so I really want this to be my final project, but since I did a simpler version of this concept I'm concerned that my additions may seem like enough to
	me to be a viable final project, however you all may not feel the same. If this is something that comes up I would be happy to come in to talk about it.