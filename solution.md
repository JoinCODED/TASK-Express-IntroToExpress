#### Setup Your Github Repository

1. Create a new repository for your backend. I'll call mine `ShopAPI`.

2. Click on `Add .gitignore` and choose `Node`. This is to add a file called `.gitignore` that has the name of directories and files that github will ignore and not add to the repository.

3. After creating the repo, clone it and let's start coding!

#### Setup Your Express App

1. Create a `package.json` using the `init` command. A `package.json` indicates that this file is an environment for nodejs:

   ```shell
   $ cd ShopAPI
   $ yarn init -y
   ```

2. Open code in VSCode and create a new file `app.js`. This will be our main file.

3. In `package.json` change the main file to `app.js`. This is just a naming convention:

   ```javascript
   {
      [...],
      "main": "app.js",
      [...]
   }
   ```

4. Install Express.

   ```shell
   $ yarn add express
   ```

5. Require `express` and create an instance of an express application.

   ```javascript
   const express = require("express");

   const app = express();
   ```

6. To see the application somewhere, we need to set our development server's port manually using the listen method and passing it the port number.

   ```javascript
   app.listen(8000);
   ```

7. Run the app.

   ```shell
   $ node app.js
   ```

   - Open the browser and go to `localhost:8000`, you'll receive a `404` status and a message saying `Cannot GET /`. Why?\
     This is because we haven't defined a `/` **route** that sends a response when it's called. But don't worry! If you get this error it means you're on the right path.
   - The terminal (no indication that the server is running)

8. The `listen()` method takes two arguments: the port number which will be `8000`, and a callback function -which is optional- that we will use to console log the port number in the terminal.

   ```javascript
   app.listen(8000, () => {
     console.log("The application is running on localhost:8000");
   });
   ```

9. Our changes are not showing. We need to restart the server every time!! (React was a blessing right?). Use `nodemon` to run the app, as it watches for any changes in the app. To install it:

   ```shell
   $ yarn global add nodemon
   ```

10. Do you miss `yarn start`? It's okay, we can still use it by writing a script in `package.json`. Add the following `"scripts"` property in `package.json`:

    ```javascript
    {
      "name": "ShopAPI",
      [...],
      "scripts": {
        "start": "nodemon app.js"
      }
    }
    ```

#### Product List Route

1. Create a new file for your data, let's call it `products.js`. Copy the data from your React app (the data should be coming from the backend now).

   ```javascript
   const products = [
     {
       id: 1,
       name: "Chocolate Chip Cookies",
       slug: "chocolate-chip-cookies",
       description: "Delicious cookie.. sold by dozen",
       price: 15,
       image:
         "https://images-gmi-pmc.edge-generalmills.com/087d17eb-500e-4b26-abd1-4f9ffa96a2c6.jpg",
     },
     {
       id: 2,
       name: "Peanut Butter Cookies",
       slug: "peanut-butter-cookies",
       description: "Delicious cookie.. sold by dozen",
       price: 3,
       image:
         "https://images-gmi-pmc.edge-generalmills.com/dcd4f799-7353-4e56-ba50-623581cba3bc.jpg",
     },
     {
       id: 3,
       name: "Salted Caramel Cookies",
       slug: "salted-caramel-cookies",
       description: "Delicious cookie.. sold by dozen",
       price: 10,
       image:
         "https://images-gmi-pmc.edge-generalmills.com/586da0ed-8a79-4390-9137-f60852ca312a.jpg",
     },
   ];
   ```

2. Export your array using `module.exports`.

   ```js
   module.exports = products;
   ```

   This is equivalent to `export default products`.

3. Require your data in `app.js`.

   ```javascript
   const products = require("./products");
   ```

4. Create a route that represents the list of cookies. Since the request wants to **fetch** data, we will use the `GET` method. We called the URL `/api/products` and then we will pass the array of products to the `res.json` method.

   ```javascript
   app.get("/products", (req, res) => {
     res.json(products);
   });
   ```

5. Test your endpoint on your web browser. Since it's a `get` method we can use the browser for testing as its default method when making a request is `GET`.
