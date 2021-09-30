# LaraApiTest
This is a simple system to demonstrate API authentication and verification when getting data or sending through data, using Laravel 7, Passport, Composer, Laravel Helpers, LAMP, Postman, Visual Studio Code. Using Linux Os.

Laravel Passport - Laravel uses the Passport library to implement a full OAuth2 server we can use for authentication in our API.(OAuth 2.0 provides consented access and restricts actions of what the client app can perform on resources on behalf of the user, without ever sharing the user's credentials.)

Installation of this project

1.Install Lamp on your pc. 
2.Composer
3.Laravel 7(Create your project at this step with laravel 7)
4.Laravel Passport(Add this to your project)
5.Laravel Helpers after (after step 3 and 4)
6.Copy project contents to your files

Edit your env file details , with details that correspond with your mysql database.
You may need to create a database called Carts_db before you do this and before migration.

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=Carts_db
DB_USERNAME=root
DB_PASSWORD=' '

Open the application in visual studio code, if you navigate to database then click  migrations, you will see all the tables that you need to help run the test, but before that you need to migrate these tables so that, they are created in the database.


How to use this project

In visual studio code,in your app ,if you navigate to routes and click on api.php all of our routes are in there divided into ,public and protected.

Now open your postman
1.Add api url – [POST]   localhost:8000/api/register ,this registers a new user.
Parameters to enter are name, email, password, password_confirmation
you will then get a token back which will be used in further authentication.
2.Add api url – [POST]   localhost:8000/api/login, here registered user logs in.
Parameters to enter are  email, password, password_confirmation
you will then get a token back which will be used in accessing a protected route as below.If you try accessing a protected routed with out logging in then your get.

{
"message": "Unauthenticated."
}


3.Add api url – [POST]   localhost:8000/api/cartCreate, here registered user  and logged in user creates a cart with contents.
Parameters to enter are  product, country and token that was received after successful login.To use this token navigate to the Authorization tab,select bearer token,place token and click send.The contents where successfully saved you will see.

{
"message": "Your product has bee saved to your cart"
}

4.Add api url – [POST]   localhost:8000/api/cartShow, here registered user  and logged in user gets to view all their carts and their contents.
No parameters to enter,the system uses the credentials of the user that is logged in,so its their view and token that was received after successful login.To use this token navigate to the Authorization tab,select bearer token,place token and click send.On success you will see.

{
"Cart": [
{
"id": 2,
"created_at": "2021-09-30T05:35:33.000000Z",
"updated_at": "2021-09-30T05:35:33.000000Z",
"product": "GreenSocks",
"country": "Greenland",
"user_id": 8
},
{
"id": 3,
"created_at": "2021-09-30T06:07:19.000000Z",
"updated_at": "2021-09-30T06:07:19.000000Z",
"product": "Green Glasses",
"country": "China",
"user_id": 8
}
]
}

5.Add api url – [PUT]   localhost:8000/api/cartUpdate/1, here registered user  and logged in user can edit/update  cart and contents.
Parameters to enter are  product, country,the id of the cart whose contents you are editing and updating and token that was received after successful login.To use this token navigate to the Authorization tab,select bearer token, place token and click send. How ever if user tries to update contents other than  thiers, this message comes through.

{
"message": "This cart is not yours to update"
}

else if they are editing their own and the update is successful.

{
"message": "Cart updated successfully"
}

6.Add api url – [DELETE]   localhost:8000/api/cartDelete/3, here registered user  and logged in user can delete cart and contents.
Parameters to enter are just the id of the cart with the contents you want to delete and token that was received after successful login.To use this token navigate to the Authorization tab,select bearer token,place token and click send.How ever if user tries to delete contents other than  thiers, this message comes through.

{
"message": "This cart is not yours to delete"
}

else if they are deleting  their own and the deletion is successful.

{
"message": "Cart deleted successfully"
}

3.Add api url – [POST]   localhost:8000/api/logout, here registered user  and logged in user is logout of the system and the token is also removed.
Parameters to enter are the token that was received after successful login. To use this token navigate to the Authorization tab,select bearer token,place token and click send.After successful login this should appear.

{
"message": "You have been successfully logged out!"
}


