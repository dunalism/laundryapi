# Laundry Management API

This application is a RESTful API built with Express.js using Role-Based Access Control (RBAC). Each endpoint is protected by an authentication system and access permissions that vary based on the role, such as `owner`, `admin`, and `user`.

## Key Features

1. **Authentication** - Register and log in to the application.
2. **Product Management** - Restricted access for `owner` only.
3. **User Management** - Full access for `owner` and `admin` only.
4. **Customer and Transaction Management** - Limited access for `owner` and `admin`.
5. **User Profile** - Accessible by all authenticated users.

---

## Prerequisites

- **Node.js** (recommended version 14 or higher)
- **Postman** (recomended)

## Installation

1. Clone this repository.
   ```bash
   git clone https://github.com/dunalism/laundryapi.git
   ```
2. Install all dependencies.
   ```bash
   npm install
   ```
3. Run the application
   ```bash
   npm start
   ```

## Testing the Application with [Postman](https://www.postman.com/downloads/)

To simplify testing of the application, you can use postman by [importing](https://learning.postman.com/docs/getting-started/importing-and-exporting/importing-data/) the available Postman collection and environment files. This will [set up](https://learning.postman.com/docs/getting-started/basics/navigating-postman/#environment-selector-and-variables-pane) all the endpoints and necessary variables for easier testing.

---

## API Documentation

For all endpoints that require authentication, you need to include the Bearer token in the headers. Here’s how to fetch data using JavaScript (fetch API).

```bash
// Example of a GET request with Bearer token
fetch('http://localhost:5000/api/v1/endpoint', {
    method: 'GET',
    headers: { 'Authorization': 'Bearer <YOUR_TOKEN_HERE>' }
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));

```

### Authentication

- **Register**  
  `POST /auth/register`  
  Register as a new user.

- **Login**  
  `POST /auth/login`  
  Log in to the system with valid credentials.

---

### Endpoints for Role `owner`

- **Update User**  
  `PUT /owner/users/:id`  
  Update user data. Accessible only by `owner`.

- **CRUD Products**
  - `POST /products` : Add a new product.
  - `PUT /products/:id` : Edit a product by ID.
  - `DELETE /products/:id` : Delete a product by ID.

---

### Endpoints for Role `owner` and `admin`

- **User Management**

  - `GET /admin/users` : Get a list of users.
  - `DELETE /admin/users/:id` : Delete a user by ID.

- **Customer Management**

  - `GET /customers` : Get a list of customers.
  - `GET /customers/:id` : Get customer details by ID.
  - `POST /customers` : Add a new customer.
  - `PUT /customers/:id` : Update customer data by ID.
  - `DELETE /customers/:id` : Delete a customer by ID.

- **Transaction Management**
  - `GET /transactions` : Get a list of transactions.
  - `GET /transactions/:id` : Get transaction details by ID.
  - `POST /transactions` : Add a new transaction.

---

### Endpoints Available to All Authenticated Users

- **User Profile**

  - `GET /users/:id` : Get user details by ID.
  - `GET /profile` : Get the profile of the currently logged-in user.
  - `PUT /profile` : Update the profile of the currently logged-in user.

- **Products**
  - `GET /products` : Get a list of products.
  - `GET /products/:id` : Get product details by ID.

---

### Important Note on Data Deletion

Since this application uses a relational database with foreign key constraints, please exercise caution when deleting users, customers, or products. If you delete a user, customer, or product that is associated with any transactions, those related transaction records will also be deleted due to the foreign key relationship. This may result in the loss of important transaction data.

---

### Built using

- [SQlite](https://www.sqlite.org/) - Database
- [Express](https://expressjs.com/) - Server Framework
- [NodeJs](https://nodejs.org/en/) - Server Environment

---

### Acknowledgements

This project is inspired by the [Enigma Laundry app API](https://github.com/jutionck/enigma-laundry-app-with-slice), an API used in the final submission for the React JS course at [Enigmacamp](https://enigmacamp.com/). Special thanks to the original creators for their work and for providing a strong foundation for this application.

### Contact

If you have any questions, want to report a bug, or provide feedback, feel free to reach out

- Email: dunalismkaizen@gmail.com
- Discord: dunalism
- Instagram: [@hmdklkhf](https://www.instagram.com/hmdklkhf)
