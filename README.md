In this task you will setup your first Express app and create one endpoint that returns a list of all products.

### 1. Setup

1. Install `nodemon` globally:

   ```shell
   $ npm install -g nodemon
   ```
2. Create a new repository, don't forget to add a `.gitignore` file of type `Node`. Then clone it.

### 2. Setup Your Express App

1. In your cloned repo, create a `package.json` file using `npm init -y`.
2. Create an `app.js` file in your project folder.
   _Don't forget to change the main file in `package.json` from `index.js` to `app.js`._
3. Install `express` and create an express application instance.
4. Bind your application to port `8000` using the `listen()` method.
5. Create a script in `package.json` that executes `nodemon app.js` when you run `npm start`.

### 3. Data Setup

1. Create a new file called `data.js`. Copy the following data in this file. _Don't forget to export it._
2. Require it in `app.js`.

### 4. Product List Route

Create a route that sends the list of your products:

1. The route's method should be `get`.
2. The URL for this route should have the following syntax: `/api/products`.
3. The response must be the list of all products.

#### Testing

Test your endpoint using the browser. It should display your array of products.
