@idct/axios-jwt-oobe-for-nuxt
=============================

Nuxt module wrapper around the `@idct/axios-jwt-oobe` package:
https://www.npmjs.com/package/@idct/axios-jwt-oobe

**pre-alpha version, for learning and debug purposes only**

Installation
============

In your nuxt project first load using npm or yarn:
```
npm install @idct/axios-jwt-oobe-for-nuxt
```

Then in `nuxt.config.json` replace `@nuxtjs/axios` with `'@idct/axios-jwt-oobe-for-nuxt`.

Later, under `axios` module config section add the required parameters - for example:
```
  axios: {
    tokenFieldName: "token",
    refreshTokenFieldName: "refresh_token",
    refreshTokenRetrievalUrl: "https://mywebsite.com/auth/refresh",
    loginActionInfo: {
      "url": "https://mywebsite.com/auth/login",
      "usernameField": "username",
      "passwordField": "password"
    },
    baseURL: 'https://mywebsite.com'
  },
```

If you wish to perform any actions on actual logout (when refresh token could not refresh token) then somewhere in your code add a callback for `onLogout`:

```js
this.$axios.onLogout(() => {
    alert("whoos you have been signed out as refresh token could not refresh the token!");
})
```

you can also use the built-in login and logout methods:
```js
this.$axios.jwtHandler.login("marian","marianspassword123")
```

```js
this.$axios.jwtHandler.logout()
```

For actual methods of the `jwtHandler` please refer to the readme of axios-jwt-oobe:
`https://github.com/ideaconnect/axios-jwt-oobe`