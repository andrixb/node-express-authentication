# Server-side authentication strategy implemented in Node/Express.js

This is a solid authorization server that can be used as a starting point for other projects.

It implements **JWT Strategy** and **Local Strategy**

It uses _Bcrypt_ for password encryption (salted + hashed passwords).

**No boilerplate has been touched.**

It uses MongoDB.

To startup `npm run dev`.

TODO:

- `signout` route is missing
- detailed step-by-step documentation

## Steps

### Create `package.json`

Type `npm init` and hit enter till the end

### Install dependencies

`npm i -S express mongoose morgan body-parser`


### Create `index.js`

Create `index.js` file as a starting point of our server in the `server` folder.

We import the libraries:
(lines 2-5)
```js
const express = require('express');
const http = require('http');
const bodyParser = require('body-parser');
const morgan = require('morgan');
```

and we setup Express first:
(line 6)
This will create an instance of express `const app = express();`

Those are middlewares:
Morgan is a login framework (when we load the page it logs incoming requests)
`app.use(morgan('combined'));``

Body Parser parses incoming requests. It parses into JSON:
`app.use(bodyParser.json({ type: '*/*' }));`


and to setup the server:

- We define a port `const port = process.env.PORT || 3090;`

- Use node API to create the server `const server = http.createServer(app);`

- We tell the server to listen to that port `server.listen(port);`

### Route handlers

### User model

### Encrypting the password with BCrypt

### JWT

`server/config.js` should look like

```js
module.exports = {
    secret: 'asdjkhasdkhasdasjkdha23479asdy983rhwed'
};
```

### Passport.js
Used for cookie auth mainly but it can be used for JWT as well.

To test routes in Postman we need to pass the token in the Header field defined in `services/passport.js`:

```js
// Setup options for JWT Strategy
const jwtOptions = {
    jwtFromRequest: ExtractJwt.fromHeader('authorization'),
    secretOrKey: config.secret
};
```

### CORS
`cors` package has been installed. Be aware you need to configure it (it's currently open to whatever address)! https://www.npmjs.com/package/cors 
