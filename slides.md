## Apps & Functions
### with

![Netlify](/img/full-logo-light.svg)<!-- .element: style="width: 50%" -->

---

![](/img/home-header.png)

---

### Easy to deploy

![](/img/steps.png)

---

## [Deploy Previews](https://www.netlify.com/docs/webhooks/#github-pull-request-comments)

![](/img/preview.png)

---

## Asset optimization

![](/img/optimization.png)

---

## [Prerendering](https://www.netlify.com/docs/prerendering)

![](/img/prerendering.png)

---

## [Proxy Redirects](https://www.netlify.com/docs/redirects)

```
# _redirects

/*    /index.html   200
/api/*  https://api.example.com/:splat  200

```

---

## [Deploy Previews](https://www.netlify.com/docs/webhooks/#github-pull-request-comments)

![](/img/preview.png)


---

## [Form Handling](https://www.netlify.com/docs/form-handling)

![](/img/forms.png)

---

## [User Management](https://www.netlify.com/docs/identity)

![](/img/identity.png)

---

## [Lambda functions](https://www.netlify.com/docs/functions)

![](/img/functions.png)

---

## 🏆 Netlify Prize 🏆

### Best Use of Netlify Functions
### $300 Amazon gift card

---

## What can functions do?

- authenticated API calls from the frontend
- webhook listeners & event-driven workflows
- chatbots & voice apps (Alexa, Google Home)
- all your awesome hackathon ideas!

---

## Add to your repo

In the UI

![](/img/functions-folder.png)

---

## Add to your repo

With a `netlify.toml` file

```
[build]
  Functions = "lambda"
```

---

## Get an endpoint

```
/.netlify/functions/<your-function-name>
```

Look, Mom, no CORS!

---

## Building Netlify Functions

---

## The Basic

Add a plain JS file to your functions folder

```
exports.handler = function(event, context, callback) {
    callback(null, {
    statusCode: 200,
    body: "Hello, World"
    });
}
```

The filename becomes the function endpoint:

```
`hello.js` ➡️ `/.netlify/functions/hello`
```

---

## [netlify-lambda](https://www.netlify.com/docs/functions/#netlify-lambda-cli)

A handy library that:

- Adds webpack and Babel
- Runs a local function server for development
- Builds your functions to single files in the functions folder

---

## [netlify-lambda](https://www.netlify.com/docs/functions/#netlify-lambda-cli)

Add to your project:

1. Install it with `npm install netlify-lambda`.
2. Include a `netlify.toml` file with the location of your [functions folder](#configuring-the-functions-folder).
3. Put the source files in a *different* folder.


---

## [Create React App Lambda](https://www.netlify.com/docs/functions/#create-react-app-lambda)

Create React App with netlify-lambda built in!

- a `src/lambda` folder for storing your functions source files
- a premade `netlify.toml` file to set the functions folder

---

## [Create React App Lambda](https://www.netlify.com/docs/functions/#create-react-app-lambda)

Create React App with netlify-lambda built in!

- built-in proxy redirect for local dev

```
 `/.netlify/functions/hello` ️ ➡️ `http://localhost:9000/hello`
```

---

## [Create React App Lambda](https://www.netlify.com/docs/functions/#create-react-app-lambda)

Clone and deploy with a single button!

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/biilmann/create-react-app-lambda)

---

## Environment Variables

- Save in the Netlify UI

![](/img/variables.png)

---

## Environment Variables

- Save in a local `.env` file (but don't push it to GitHub!)
- Use `dotenv` to include the variables in your code

```
const SECRET_API_KEY = process.env.SECRET_API_KEY;
```

---

## Environment Variables

- Pass API calls through your function without exposing your key!

![](/img/weather-call.png)

[github.com/mattburrell/wishyouwerehere](https://github.com/mattburrell/wishyouwerehere)
