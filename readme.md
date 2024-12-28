# Quickpage

Quickpage is a GitHub template for creating single-page-application with front-end routing and JSX. See demo at official page <https://quickpage.foxdebug.com>.

## Usage

Create github repository using this template.

## Documentation

### Start server

To start the server run the following bash command

```bash
: yarn start
```

To start the dev-server run the following bash command

```bash
: yarn start-dev
```

### Build the application

```bash
: yarn build-release
```

The server uses 'NodeJs' and 'ExpressJs' for serving files. You can edit the server src code in `server` directory.

### Routing

```javascript
import Router from 'lib/Router';
```

Add routes.

```javascript
Router.add('/home', (params, queries) => {
  // render home
});
```

Start route.

```javascript
Router.listen();
```

#### Create separate routing page

Create a router page

```bash
touch adminRouter.js
```

Initialize router page.

```javascript
// adminRouter.js
import Router from 'lib/RouterExtension';

const router = new Router('/admin');

// routes

export default router;
```

Add middle function to filter routes.

```javascript
Router.beforeNavigate((url, next) => {
  // url -> current url
  // next -> callback function
  // call next function to proceed
});
```

Add a route.

```javascript
Router.add('home', (params, queries) => {
  // render '/base-route/home'
});
```

Add router to main Router.

```javascript
import adminRouter from './adminRouter';
import Router from 'lib/Router';

Router.use(adminRouter);
Router.listen();
```
