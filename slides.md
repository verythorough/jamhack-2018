## Hacking on the JAMstack
### with

![Netlify](/img/full-logo-light.svg)<!-- .element: style="width: 50%" -->

---

### How do I even JAMstack?

![](https://i.pinimg.com/originals/02/eb/0a/02eb0a01c39b4b07de7f3aa6a081ef5c.png)

---

### A full-stack app

![](https://static.meijer.com/Media/005/15000/0051500000557_a1c1_0600.png)

---

### A JAMstack app

![](/img/dougiejam.png)

---

### Backend APIs

![](https://images-na.ssl-images-amazon.com/images/I/818pymVNdXL._SY606_.jpg)<!-- .element: style="float: left" -->

---

### Backend APIs

![](https://images-na.ssl-images-amazon.com/images/I/818pymVNdXL._SY606_.jpg)<!-- .element: style="float: left" -->

#### Third-party<!-- .element: style="margin-top: 1.5em" -->

- Formspree
- Clarifai
- Pilon
- Any other API

---

### Backend APIs

![](https://images-na.ssl-images-amazon.com/images/I/818pymVNdXL._SY606_.jpg)<!-- .element: style="float: left" -->

#### Build your own<!-- .element: style="margin-top: 1.5em" -->

- Fauna
- Hasura
- Netlify Functions
- Any other backend or cloud function

---

### Frontend

![](https://s3.us-east-2.amazonaws.com/jms-s3-cx-rel-p-pmc4/assets/smuckers/images/products/13846.jpeg)<!-- .element: style="float: left" -->

#### Frameworks<!-- .element: style="margin-top: 1.5em" -->

- React
- Vue
- Angular
- Any other framework
- None at all

---

### Frontend

![](https://s3.us-east-2.amazonaws.com/jms-s3-cx-rel-p-pmc4/assets/smuckers/images/products/13846.jpeg)<!-- .element: style="float: left" -->

#### Next level: SSR at build-time<!-- .element: style="margin-top: 1em" -->

- Gatsby
- React Static
- VuePress
- Gridsome
- Jekyll
- Hugo
- [Over 400 others](https://www.staticgen.com/)

---

![](/img/home-header.png)

---

### Push to build

![](/img/steps.png)

---

### Deploy worldwide

![](/img/adn.png)

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

## [Form Handling](https://www.netlify.com/docs/form-handling)

![](/img/forms.png)

---

## [User Management](https://www.netlify.com/docs/identity)

![](/img/identity.png)

---

## [Lambda functions](https://www.netlify.com/docs/functions)

![](/img/functions.png)

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

## Environment Variables

Save in the Netlify UI

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

Make API calls without exposing your key!

```
// Send greeting to Slack
  return fetch(process.env.SLACK_WEBHOOK_URL, {
    headers: {
      "content-type": "application/json"
    },
    method: "POST",
    body: JSON.stringify({ text: `${name} says hello!` })
  })
    .then(() => ({
      statusCode: 200,
      body: `Hello, ${name}! Your greeting has been sent to Slack 👋`
    }))
    .catch(error => ({
      statusCode: 422,
      body: `Oops! Something went wrong. ${error}`
    }));
};
```

---

## Examples to Get You Started

[Create React App Lambda](https://www.netlify.com/docs/functions/#create-react-app-lambda)

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/biilmann/create-react-app-lambda)

_Create React App with netlify-lambda built in_

---

## Examples to Get You Started

[Netlify Function Example](https://github.com/netlify/netlify-functions-example) [![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/biilmann/create-react-app-lambda)

- Framework-free setup with netlify-lambda
- [Demo site and guide](https://functions-playground.netlify.com/) with sample functions from basic to powerful
- Lots more example repos in the README

---

## Features in Both Examples

- a `src/lambda` folder for storing your functions source files
- a premade `netlify.toml` file to set the functions folder
- built-in proxy redirect for local dev

```
 `/.netlify/functions/hello` ️ ➡️ `http://localhost:9000/hello`
```

---

## More Resources

- [JAMstack vs Isomorphic Server Side Rendering](https://www.netlify.com/blog/2017/06/06/jamstack-vs-isomorphic-server-side-rendering/)
- [How to add Netlify Identity service to React projects](https://www.netlify.com/blog/2017/10/30/how-to-add-netlify-identity-service-to-react-projects/)
- [How to setup serverless OAuth Flows with Netlify Functions & Intercom](https://www.netlify.com/blog/2018/07/30/how-to-setup-serverless-oauth-flows-with-netlify-functions--intercom/)
- [Building Serverless CRUD apps with Netlify Functions & FaunaDB](https://www.netlify.com/blog/2018/07/09/building-serverless-crud-apps-with-netlify-functions--faunadb/)
