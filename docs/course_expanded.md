This **30-day Express.js crash course** is structured with an **API-first approach** and focuses on **JWT authentication**. It provides hands-on daily *mini-projects* or tasks, complete with code snippets, reference resources, and fallback reading for fundamentals. This course is designed for experienced software engineers, allowing for just-in-time diving or deeper learning.

Here’s your **33-day Express.js crash course**, structured API-first with JWT authentication, and hands-on daily *mini-projects* or tasks. Each day features a practical prompt with code snippets, reference resources, and fallback reading for fundamentals—perfect for just-in-time diving or deeper learning, tailored for a senior engineer like you.

## **Days 1–3: Foundations & Project Setup**

**Day 1: Scaffold the API**

- **Task:** Initialize the API project with Express, set up an entrypoint (`app.js`), and add a health check endpoint at `/health`.
- **Snippet:**
    ```js
    const express = require('express');
    const app = express();
    app.get('/health', (req, res) => res.json({ status: 'ok' }));
    app.listen(3000, () => console.log('Server running'));
    ```
- **Resources:** [Express Beginner Guide](https://expressjs.com/en/starter/installing.html)
- **Reading:** Understand the request/response flow.

**Day 2: Basic Routing & API Design**

- **Task:** Add a `/hello` endpoint that responds with a JSON `{ message: "Hello, World!" }`. Discuss RESTful naming conventions.
- **Snippet:**
    ```js
    app.get('/hello', (req, res) => res.json({ message: 'Hello, World!' }));
    ```
- **Resources:** [REST resource naming conventions](https://restfulapi.net/resource-naming/)
- **Reading:** [Express Routing](https://expressjs.com/en/guide/routing.html)

**Day 3: API Project Structure**

- **Task:** Organize your project: `routes/`, `controllers/`, `middleware/`.
- **Snippet:** Move `/health` handler to `routes/health.js`.
- **Resources:** [Structural best practices](https://dev.to/abdelmjd/clean-architecture-with-node-js-2j1a)
- **Reading:** [Express Application Structure](https://expressjs.com/en/advanced/best-practice-structure.html)

## **Days 4–6: Handling and Parsing Data**

**Day 4: Parsing JSON & URL-Encoded Requests**

- **Task:** Configure `express.json()` and `express.urlencoded()` middleware globally to handle different request body types.
- **Snippet:**
    ```js
    app.use(express.json());
    app.use(express.urlencoded({ extended: true })); // For parsing application/x-www-form-urlencoded
    ```
- **Resources:** [Request handling docs](https://expressjs.com/en/api.html#express.json), [express.urlencoded()](https://expressjs.com/en/api.html#express.urlencoded)
- **Reading:** What is the `req.body` object? How do `application/json` and `application/x-www-form-urlencoded` differ?

**Day 5: Route Parameters & Query Strings**

- **Task:** Add `/greet/:name` endpoint, returns personalized greeting based on URL param and a `lang` query.
- **Snippet:**
    ```js
    app.get('/greet/:name', (req, res) => {
      const lang = req.query.lang || 'en';
      const msg = lang === 'es' ? `¡Hola, ${req.params.name}!` : `Hello, ${req.params.name}!`;
      res.json({ message: msg });
    });
    ```
- **Resources:** [Route Parameters](https://expressjs.com/en/guide/routing.html#route-parameters)
- **Reading:** [req.params and req.query](https://expressjs.com/en/api.html#req.query)

**Day 6: Serving Static Content (API Docs)**

- **Task:** Serve API documentation from `/docs` using `express.static`.
- **Snippet:**
    ```js
    app.use('/docs', express.static('docs'));
    ```
- **Resources:** [Serving static files](https://expressjs.com/en/starter/static-files.html)
- **Reading:** Where to host API docs? OpenAPI/Swagger basics.

## **Days 7–9: Middleware Patterns**

**Day 7: Custom Middleware**

- **Task:** Add middleware to log incoming requests (`console.log(`${req.method} ${req.url}`)`).
- **Snippet:**
    ```js
    app.use((req, res, next) => {
      console.log(`${req.method} ${req.url}`);
      next();
    });
    ```
- **Resources:** [Middleware guide](https://expressjs.com/en/guide/using-middleware.html)

**Day 8: Third-party Middleware (CORS, Logging)**

- **Task:** Integrate `cors` and `morgan` for CORS and request logging.
- **Snippet:**
    ```js
    const cors = require('cors');
    const morgan = require('morgan');
    app.use(cors());
    app.use(morgan('dev'));
    ```
- **Resources:** [CORS in Express](https://expressjs.com/en/resources/middleware/cors.html)

**Day 9: Synchronous Error Handling Middleware**

- **Task:** Add a centralized error handler for synchronous errors; trigger it with a `/fail` endpoint.
- **Snippet:**
    ```js
    app.get('/fail', (req, res, next) => {
      throw new Error('Synchronous Failure!'); // This will be caught by the error middleware
    });
    app.use((err, req, res, next) => {
      console.error(err.stack); // Log the error stack for debugging
      res.status(500).json({ error: err.message });
    });
    ```
- **Resources:** [Error handling](https://expressjs.com/en/guide/error-handling.html)

**Day 10: Asynchronous Error Handling**

- **Task:** Implement robust error handling for asynchronous operations (e.g., database calls, API requests) within routes.
- **Snippet:**
    ```js
    // Option 1: Using a utility to wrap async route handlers
    const asyncHandler = fn => (req, res, next) => {
      Promise.resolve(fn(req, res, next)).catch(next);
    };

    app.get('/async-fail', asyncHandler(async (req, res, next) => {
      // Simulate an async operation that throws an error
      await new Promise(resolve => setTimeout(resolve, 100));
      throw new Error('Asynchronous Failure!');
    }));

    // Option 2: Using try-catch within the async function
    app.get('/another-async-fail', async (req, res, next) => {
      try {
        await new Promise(resolve => setTimeout(resolve, 100));
        throw new Error('Another Asynchronous Failure!');
      } catch (err) {
        next(err); // Pass the error to the error handling middleware
      }
    });
    ```
- **Resources:** [Handling Errors in Express.js Async Functions](https://expressjs.com/en/guide/error-handling.html#catching-errors-in-asynchronous-code)
- **Reading:** Understand `try/catch` with `async/await` and how `next(err)` passes errors to the middleware. Consider `express-async-errors` package for simpler async error handling."


## **Days 11–13: Input Validation**

**Day 11: Using express-validator**

- **Task:** Install `express-validator`, require an email in POST `/users`.
- **Snippet:**
    ```js
    const { body, validationResult } = require('express-validator');
    app.post('/users', body('email').isEmail(), (req, res) => {
      const errors = validationResult(req);
      if (!errors.isEmpty()) return res.status(400).json({ errors: errors.array() });
      res.sendStatus(201);
    });
    ```
- **Resources:** [express-validator docs](https://express-validator.github.io/docs/)

**Day 11: Custom Validation Logic & `checkSchema`**

- **Task:** Require password min length in `/users` POST. Additionally, use `checkSchema` to define validation rules for a more complex user registration payload (e.g., `username`, `email`, `password`).
- **Snippet:**
    ```js
    // For password min length
    body('password').isLength({ min: 8 })

    // Using checkSchema for a more complex payload
    const { checkSchema } = require('express-validator');
    app.post('/register', checkSchema({
      username: {
        notEmpty: { errorMessage: 'Username is required' },
        isLength: { options: { min: 3 }, errorMessage: 'Username must be at least 3 characters' }
      },
      email: {
        isEmail: { errorMessage: 'Invalid email address' }
      },
      password: {
        isLength: { options: { min: 8 }, errorMessage: 'Password must be at least 8 characters' }
      }
    }), (req, res) => {
      const errors = validationResult(req);
      if (!errors.isEmpty()) return res.status(400).json({ errors: errors.array() });
      res.sendStatus(201);
    });
    ```
- **Reading:** [Custom validators](https://express-validator.github.io/docs/custom-validator-sanitizer/), [checkSchema documentation](https://express-validator.github.io/docs/check-schema-api.html)
- **Further Reading:** `checkSchema` is a powerful feature for defining complex validation rules concisely. Explore its full capabilities for nested objects, conditional validation, and custom error messages.

**Day 12: Sanitization**

- **Task:** Sanitize input before use.
- **Snippet:**
    ```js
    body('name').trim().escape()
    ```
- **Reading:** [Sanitization methods](https://express-validator.github.io/docs/sanitization/)

## **Days 16–19: Environment Configuration & Auth API with JWTs**

**Day 13: Environment Configuration with `dotenv`**

- **Task:** Implement environment variable loading using `dotenv` to manage sensitive information (e.g., database credentials, API keys, JWT secrets) and configuration settings.
- **Snippet:**
    ```js
    // In your main app.js or a config file
    require('dotenv').config();
    const jwtSecret = process.env.JWT_SECRET; // Access environment variables
    ```
- **Resources:** [dotenv npm package](https://www.npmjs.com/package/dotenv), [12 Factor App - Config](https://12factor.net/config)
- **Reading:** Why are environment variables crucial for application security and deployment? How do you handle different environments (development, production)?

**Day 14: Intro to Passport.js**

- **Task:** Understand the role of Passport.js in authentication. Install `passport` and `passport-jwt`.
- **Snippet:**
    ```js
    const passport = require('passport');
    const JwtStrategy = require('passport-jwt').Strategy;
    const ExtractJwt = require('passport-jwt').ExtractJwt;

    app.use(passport.initialize());
    ```
- **Resources:** [Passport.js documentation](https://www.passportjs.org/docs/), [Passport-JWT documentation](https://www.passportjs.org/packages/passport-jwt/)
- **Reading:** How does Passport.js simplify authentication strategies? What is a "strategy" in Passport.js?

**Day 15: Passport.js JWT Strategy**

- **Task:** Configure Passport.js to use a JWT strategy for authenticating users based on a token.
- **Snippet:**
    ```js
    const opts = {
      jwtFromRequest: ExtractJwt.fromAuthHeaderAsBearerToken(),
      secretOrKey: process.env.JWT_SECRET // Use your JWT secret from .env
    };

    passport.use(new JwtStrategy(opts, (jwt_payload, done) => {
      // In a real app, you'd look up the user in your database here
      // For this example, we'll just assume the user is valid
      if (jwt_payload.userId) {
        return done(null, { id: jwt_payload.userId });
      } else {
        return done(null, false);
      }
    }));

    // Example of using the strategy in a route
    app.get('/profile', passport.authenticate('jwt', { session: false }), (req, res) => {
      res.json({ message: 'Welcome!', user: req.user });
    });
    ```
- **Resources:** [Passport-JWT example](https://www.passportjs.org/packages/passport-jwt/#usage)
- **Reading:** How does `passport.authenticate()` work? What is `session: false`?

**Day 16: Setup JWT Auth with jsonwebtoken**

**Day 16: Setup JWT Auth with jsonwebtoken**

- **Task:** Install `jsonwebtoken`, create `/auth/login` route to return token.
- **Snippet:**
    ```js
    const jwt = require('jsonwebtoken');
    app.post('/auth/login', (req, res) => {
      // Assume successful login
      const token = jwt.sign({ userId: 1 }, 'secret', { expiresIn: '1h' });
      res.json({ token });
    });
    ```
- **Resources:** [jsonwebtoken usage](https://github.com/auth0/node-jsonwebtoken)

**Day 14: JWT Auth Middleware**

- **Task:** Middleware to verify token in `Authorization: Bearer ...`
- **Snippet:**
    ```js
    function auth(req, res, next) {
      const token = req.headers.authorization?.split(' ')[1];
      if (!token) return res.sendStatus(401);
      jwt.verify(token, 'secret', (err, user) => {
        if (err) return res.sendStatus(403);
        req.user = user;
        next();
      });
    }
    ```
- **Reading:** [JWT best practices](https://jwt.io/introduction/)

**Day 15: Protected Routes**

- **Task:** Secure `/me` endpoint with the `auth` middleware.
- **Snippet:**
    ```js
    app.get('/me', auth, (req, res) => {
      res.json({ user: req.user });
    });
    ```

**Day 16: Password Hashing**

- **Task:** Store hashed passwords using `bcryptjs`.
- **Snippet:**
    ```js
    const bcrypt = require('bcryptjs');
    const hash = await bcrypt.hash(req.body.password, 10);
    const valid = await bcrypt.compare(req.body.password, hash);
    ```
- **Resources:** [bcrypt docs](https://github.com/dcodeIO/bcrypt.js/)

## **Days 19–22: API Expansion & RBAC**

**Day 20: Route-Level Authorization**

- **Task:** Add "admin" property to JWT. Create middleware to allow only admin users to access `/admin`.
- **Snippet:**
    ```js
    function isAdmin(req, res, next) {
      if (!req.user?.admin) return res.sendStatus(403);
      next();
    }
    app.get('/admin', auth, isAdmin, (req, res) => res.send('Secret admin data'));
    ```

**Day 18: Organize with Routers**

- **Task:** Refactor routes for users, auth, and admin into separate files using `express.Router()`.
- **Resources:** [Router docs](https://expressjs.com/en/guide/routing.html#express-router)

**Day 19: API Versioning**

- **Task:** Mount your API under `/api/v1/`.
- **Snippet:**
    ```js
    app.use('/api/v1', router);
    ```
- **Resources:** [API Versioning](https://medium.com/@jeffandersen/building-a-node-js-rest-api-with-express-4-and-mongoose-902c51d53f19)

**Day 20: OpenAPI/Swagger Docs**

- **Task:** Use `swagger-ui-express` and `swagger-jsdoc` to create live API docs at `/api-docs`.
- **Resources:** [swagger-ui-express example](https://www.npmjs.com/package/swagger-ui-express)

## **Days 24–26: Security**

**Day 21: Helmet**

- **Task:** Use `helmet` middleware.
- **Snippet:**
    ```js
    const helmet = require('helmet');
    app.use(helmet());
    ```
- **Reading:** [Helmet for Express](https://helmetjs.github.io/)

**Day 22: Rate Limiting**

- **Task:** Use `express-rate-limit` to protect `/auth/login`.
- **Snippet:**
    ```js
    const rateLimit = require('express-rate-limit');
    app.use('/auth/login', rateLimit({ windowMs: 15 * 60 * 1000, max: 10 }));
    ```
- **Resources:** [Rate limit docs](https://www.npmjs.com/package/express-rate-limit)

**Day 23: HTTPS Local Dev**

- **Task:** Explore using native `https` module and self-signed cert for local dev.
- **Resources:** [NodeJS HTTPS server](https://nodejs.org/api/https.html)

**Day 27: Secure Cookies**

- **Task:** Understand how to set and manage secure, HTTP-only cookies in Express. This is crucial for session management or storing non-sensitive tokens securely.
- **Snippet:**
    ```js
    // Setting a secure, HTTP-only cookie
    res.cookie('token', 'your_jwt_token', {
      httpOnly: true, // Prevents client-side JavaScript from accessing the cookie
      secure: process.env.NODE_ENV === 'production', // Send cookie only over HTTPS in production
      maxAge: 3600000, // Cookie expiration in milliseconds (1 hour)
      sameSite: 'Lax' // Protection against CSRF attacks
    });

    // Clearing a cookie
    res.clearCookie('token');
    ```
- **Resources:** [Express `res.cookie()` documentation](https://expressjs.com/en/api.html#res.cookie), [MDN Web Docs: `Set-Cookie` header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie)
- **Reading:** What are the `httpOnly`, `secure`, `SameSite`, and `Max-Age`/`Expires` cookie attributes? Why are they important for security?

## **Days 28–30: Robustness**

**Day 28: Logging and Monitoring**

- **Task:** Integrate `morgan` logs with a rotating file stream.
- **Snippet:** [Morgan docs](https://www.npmjs.com/package/morgan)

**Day 25: Error Reporting**

- **Task:** Plug in an error reporting service (e.g., Sentry) for production.
- **Resources:** [Sentry for Node](https://docs.sentry.io/platforms/node/)

**Day 26: Deploy to Render/Heroku**

- **Task:** Deploy API to Render or Heroku; configure environment variables.
- **Reading:** [Heroku + Express quickstart](https://devcenter.heroku.com/articles/getting-started-with-nodejs)

## **Days 31–33: Testing & External APIs**

**Day 31: Automated API Testing**

- **Task:** Use Jest and Supertest to write integration tests for `/hello`.
- **Snippet:**
    ```js
    const request = require('supertest');
    // ... test example
    ```
- **Resources:** [Jest + Supertest](https://jestjs.io/docs/getting-started)

**Day 32: Consuming External APIs**

- **Task:** Use `axios` to create an `/weather` route that fetches data from an external API.
- **Snippet:**
    ```js
    const axios = require('axios');
    app.get('/weather', async (req, res) => {
      const response = await axios.get('https://api.weather.com/...');
      res.json(response.data);
    });
    ```
- **Resources:** [axios docs](https://github.com/axios/axios)

**Day 33: API Documentation with Swagger**

- **Task:** Expand your OpenAPI docs with models and endpoint descriptions.
- **Resources:** [OpenAPI Specification](https://swagger.io/specification/)

## **Day 30: Capstone & Review**

- **Task:** Refactor and finalize API, run all tests, and deploy. Write a self-assessment: which patterns were unfamiliar? Where are your new weak spots? Set a learning goal (e.g., add OAuth/SSO, dive into websockets, or profile performance).

**Tip:** Each day, spend 5–7 minutes on the project task/code—and 2–5 minutes on reading the resource links for conceptual backup.

Let me know if you want example solutions, more starter code for any day, or deeper dive reading on specific big-ticket items!