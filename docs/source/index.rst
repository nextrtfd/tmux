=======================================================
Careem Pay Merchant Plugins - NodeJS API Documentation
=======================================================

**Disclaimer:** This project is experimental and the APIs are not considered stable.

The **Careem Pay Merchant Plugins** repository offers server-side code plugins to simplify integration with the **Careem Pay Merchant API**. Merchants can configure their credentials in an `.env` file and access CPay Merchant APIs with minimal additional code.

---------------------------
Overview
---------------------------

The **Careem Pay Merchant Plugin** for NodeJS allows merchants to integrate with Careem Pay's payment services easily. By configuring environment credentials, merchants can perform various payment-related operations without extensive setup.

---------------------------
Prerequisites
---------------------------

To test the API on localhost, you need to have:

- **NodeJS** (Latest LTS version recommended)
- **NPM** or **Yarn** for package management
- **Postman** to test endpoints
- **Careem Pay Merchant Onboarding**:
  - A registered merchant account on CPay.
  - Your **Client ID** and **Client Secret** issued by CPay.

---------------------------
Installation and Setup
---------------------------

Follow the steps below to set up the project:

1. **Clone the Repository**:
   - Download or clone the source code from the repository.

2. **Install Dependencies**:
   - The repository contains the source code but does not include `node_modules`. At the root directory (where `index.js` is located), run either of the following commands:

   .. code-block:: bash

       npm install

   or

   .. code-block:: bash

       yarn

3. **Configure Environment Variables**:
   - Set up your `.env` file with the following variables:

     - `CLIENT_ID`: Your Careem Pay Client ID.
     - `CLIENT_SECRET`: Your Careem Pay Client Secret.
     - Any other required API-specific configurations.

4. **Start the Server**:
   - To simulate the endpoint on localhost, use one of the following commands:

   .. code-block:: bash

       npm start

   or

   .. code-block:: bash

       yarn start

5. **Testing with Postman**:
   - Use **Postman** to send requests to the endpoint and verify functionality.

---------------------------
API Endpoints
---------------------------

The plugin provides several endpoints for integrating with the Careem Pay Merchant API. Below is a general structure; refer to the plugin documentation for details on each endpoint.

### Authentication Endpoint

   **Endpoint:** `/auth`
   
   **Method:** `POST`
   
   **Description:** This endpoint authenticates the merchant using the client credentials provided in the `.env` file.

   - **Request Body**:
     
     - `client_id`: Your Careem Pay Client ID.
     - `client_secret`: Your Careem Pay Client Secret.
   
   - **Response**:
     
     - `token`: Access token required for subsequent API calls.
     - `expires_in`: Token expiration time.

### Payment Processing Endpoint

   **Endpoint:** `/process-payment`
   
   **Method:** `POST`
   
   **Description:** Initiates a payment transaction for the merchant's order.

   - **Request Body**:
     
     - `amount`: The transaction amount.
     - `currency`: Currency in which the payment is made.
     - `payment_method`: Preferred payment method for the transaction.
   
   - **Response**:
     
     - `transaction_id`: Unique ID for the payment transaction.
     - `status`: Status of the payment (e.g., `success`, `pending`, `failed`).
     - `message`: Description or message about the transaction result.

### Refund Endpoint

   **Endpoint:** `/refund`
   
   **Method:** `POST`
   
   **Description:** Processes a refund for a previously completed transaction.

   - **Request Body**:
     
     - `transaction_id`: The unique ID of the transaction to be refunded.
     - `amount`: Amount to refund (if partial refund is supported).
   
   - **Response**:
     
     - `refund_id`: Unique ID for the refund transaction.
     - `status`: Status of the refund (e.g., `processed`, `failed`).
     - `message`: Description or message regarding the refund status.

---------------------------
Running and Testing Locally
---------------------------

To test the plugin on your local machine:

1. Run the plugin using the start command:

   .. code-block:: bash

       npm start

2. Open **Postman** and configure it to interact with the plugin’s endpoints. Use the authentication endpoint to retrieve an access token, and include this token in the headers of subsequent API requests.

---------------------------
Error Handling
---------------------------

The API includes standard error codes to identify the issues merchants may encounter:

- **400 Bad Request**: The request was invalid, possibly due to missing or incorrect parameters.
- **401 Unauthorized**: Authentication failure, either due to an invalid client ID, client secret, or expired token.
- **403 Forbidden**: The merchant does not have permission to access the requested resource.
- **500 Internal Server Error**: An error occurred on the server side. Contact support if the issue persists.

---------------------------
Contribution Guidelines
---------------------------

If you would like to improve this plugin:

1. **Fork the Repository**:
   - Clone the repository to make your modifications.

2. **Follow Contribution Guidelines**:
   - Adhere to the contribution standards outlined in the repository documentation.
   - Test your changes locally before submitting a pull request.

3. **Submit a Pull Request**:
   - Provide a detailed description of your changes, including any new features or bug fixes.

---------------------------
Conclusion
---------------------------

The **Careem Pay Merchant Plugin** for NodeJS simplifies integration with Careem Pay's API by offering ready-to-use endpoints for common payment functions. With minimal setup, merchants can integrate essential payment services into their applications securely and efficiently.

=======================================================
