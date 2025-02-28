# Shops-Mart
ecommerce store

API Client for E-Commerce Application

This repository provides a JavaScript API client for interacting with the backend services of an e-commerce platform. The API client supports authentication, cart management, product management, wishlist management, user management, caching, retry logic, and timeout handling. The client is designed to be flexible and optimized for efficient interactions with the backend.

Features

Authentication: Login and logout functionality for users.
Cart Management: Add, update, delete cart items, and notify subscribers when the cart changes.
Product Management: Fetch all products, fetch product by ID, and CRUD operations for products.
User Management: Fetch all users, delete users, and manage user profiles.
Wishlist Management: Add, remove, and fetch wishlist items.
Caching: Cache API responses for frequently fetched data to reduce unnecessary requests.
Retries: Retry failed requests up to a configurable maximum number of times with a delay between attempts.
Timeouts: Requests are automatically aborted if they take longer than a specified timeout duration.
Request Queuing: Prevents duplicate requests by queuing requests with the same parameters.

Table of Contents

Installation
Usage
API Endpoints
Authentication
Cart
Products
Users
Wishlist
Search
Configuration
Cache Duration
Retries and Delay
Timeout
Error Handling
Contributing
License

Installation

To get started, simply include the JavaScript file in your project or import it as a module. You can use it in any modern JavaScript environment (browser, Node.js).

bash
Copy
npm install --save api-client
Then, you can import and use it:

javascript
Copy
import { loginUser, fetchAllProducts, addCartItem } from 'api-client';
Usage
Here’s a basic example of how you can use the functions in this client:

javascript
Copy
import { loginUser, fetchAllProducts, addCartItem } from 'api-client';

// Login a user
const email = 'user@example.com';
const password = 'password123';

loginUser(email, password)
  .then(role => {
    console.log(`Logged in as ${role}`);
  })
  .catch(error => {
    console.error('Login failed:', error);
  });

// Fetch all products
fetchAllProducts()
  .then(products => {
    console.log('Products:', products);
  })
  .catch(error => {
    console.error('Failed to fetch products:', error);
  });

// Add item to cart
const newItem = {
  productId: '12345',
  quantity: 2,
};

addCartItem(newItem)
  .then(result => {
    console.log('Item added to cart:', result);
  })
  .catch(error => {
    console.error('Failed to add item to cart:', error);
  });
  
API Endpoints

Authentication
Login:
javascript
Copy
loginUser(email, password)
Logs in the user and returns the user’s role (e.g., admin, customer).

Logout:
javascript
Copy
logoutUser()
Logs out the current user.

Cart

Fetch All Cart Items:
javascript
Copy
fetchAllCartItems()
Fetches all items currently in the user’s cart.

Add Cart Item:
javascript
Copy
addCartItem(item)
Adds a product to the cart. The item should be an object containing the product details.

Update Cart Item:
javascript
Copy
updateCartItem(itemId, item)
Updates an existing item in the cart.

Delete Cart Item:
javascript
Copy
deleteCartItem(itemId)
Removes an item from the cart.

Cart Subscription:
javascript
Copy
subscribeToCart(callback)
Allows other parts of your application to subscribe to cart changes. The callback function will be invoked when the cart is updated.

Products

Fetch All Products:
javascript
Copy
fetchAllProducts()
Fetches all products from the catalog.

Fetch Product by ID:
javascript
Copy
fetchProductById(id)
Fetches a single product by its ID.

Add Product:
javascript
Copy
addProduct(product)
Adds a new product to the catalog.

Update Product:
javascript
Copy
updateProduct(id, product)
Updates an existing product in the catalog.

Delete Product:
javascript
Copy
deleteProduct(id)
Deletes a product from the catalog.

Users

Fetch All Users:
javascript
Copy
fetchAllUsers()
Fetches all users from the platform.

Delete User:
javascript
Copy
deleteUser(userId)
Deletes a user from the platform.

Fetch User Profile:
javascript
Copy
fetchUserProfile(email)
Fetches the profile of a user by email.

Update User Profile:
javascript
Copy
updateUserProfile(email, data)
Updates the profile of a user.

Wishlist

Fetch Wishlist:
javascript
Copy
fetchWishlist(email)
Fetches the wishlist of the user.

Add to Wishlist:
javascript
Copy
addToWishlist(email, item)
Adds an item to the user’s wishlist.

Remove from Wishlist:
javascript
Copy
removeFromWishlist(email, productId)
Removes an item from the user’s wishlist.

Search

Search Products:
javascript
Copy
searchProducts(keyword)
Searches for products based on a keyword.

Configuration

Cache Duration
The cache duration for API responses can be configured with CACHE_DURATION. It is set to 5 minutes by default:

javascript
Copy
const CACHE_DURATION = 5 * 60 * 1000; // 5 minutes
Retries and Delay
The client will retry a failed request up to a maximum number of retries (MAX_RETRIES) and introduce a delay between retries (RETRY_DELAY):

javascript
Copy
const MAX_RETRIES = 3; // Maximum number of retries
const RETRY_DELAY = 1000; // Delay between retries in milliseconds

Timeout

Requests are automatically aborted if they take longer than the configured timeout (TIMEOUT_DURATION):

javascript
Copy
const TIMEOUT_DURATION = 5000; // 5 seconds

Error Handling

HTTP Errors: The client throws an error when an HTTP request fails, including status codes such as 404 or 500.
Timeout Errors: If a request exceeds the defined timeout duration, an error is thrown indicating a timeout.
Invalid Data: If the data returned from an API is not in the expected format, an error will be thrown.
Retries: The client will attempt to retry failed requests according to the retry configuration.
Contributing
If you would like to contribute to this project, please fork the repository, make your changes, and submit a pull request.

Fork the repository.

Create a new branch for your changes.
Commit your changes.
Push your changes to your forked repository.
Open a pull request.
License
This project is licensed under the MIT License - see the LICENSE file for details.
