<!-- TITLE/ -->
# nuxt-mail
<!-- /TITLE -->

<!-- BADGES/ -->
[![NPM version](https://img.shields.io/npm/v/nuxt-mail.svg)](https://npmjs.org/package/nuxt-mail)
![Linux macOS Windows compatible](https://img.shields.io/badge/os-linux%20%7C%C2%A0macos%20%7C%C2%A0windows-blue)
[![Build status](https://img.shields.io/github/workflow/status/undefined/build)](https://github.com/undefined/actions)
[![Coverage status](https://img.shields.io/coveralls/undefined)](https://coveralls.io/github/undefined)
[![Dependency status](https://img.shields.io/david/undefined)](https://david-dm.org/undefined)
![Renovate enabled](https://img.shields.io/badge/renovate-enabled-brightgreen)

<a href="https://www.buymeacoffee.com/dword">
  <img
    src="https://www.buymeacoffee.com/assets/img/guidelines/download-assets-sm-2.svg"
    alt="Buy Me a Coffee"
    height="32"
  >
</a><a href="https://gitpod.io/#https://github.com/undefined">
  <img src="https://gitpod.io/button/open-in-gitpod.svg" alt="Open in Gitpod">
</a>
<a href="https://paypal.me/SebastianLandwehr">
  <img
    src="https://upload.wikimedia.org/wikipedia/commons/b/b5/PayPal.svg"
    alt="PayPal"
    height="30"
  >
</a>
<!-- /BADGES -->

<!-- DESCRIPTION/ -->
Adds mail sending capability to a Nuxt app. Adds a server route, an injected variable, and uses nodemailer to send emails
<!-- /DESCRIPTION -->

<!-- INSTALL/ -->
## Install

```bash
# NPM
$ npm install nuxt-mail

# Yarn
$ yarn add nuxt-mail
```
<!-- /INSTALL -->

## Usage

Add the module to your `nuxt.config.js`. It is recommended to also install the `@nuxtjs/axios` module (see below):
```js
export default {
  modules: [
    '@nuxtjs/axios',
    ['nuxt-mail', {
      smtp: {
        host: "smtp.example.com",
        port: 587,
      },
    },
  ],
  // or use the top-level option:
  mail: {
    smtp: {
      host: "smtp.example.com",
      port: 587,
    },
  },
}
```

The `smtp` options are required and directly passed to [nodemailer](https://nodemailer.com/smtp/). Refer to their documentation for available options.

The module adds a `/mail/send` post route, which can be invoked via `$axios`:
```js
// Inside a component
this.$axios.$post('/mail/send', {
  from: 'John Doe',
  subject: 'Incredible',
  text: 'This is an incredible test message',
  to: 'johndoe@gmail.com',
})
```

The module also injects the `$mail` variable, which makes it even easier:
```js
// Inside a component
this.$mail.send({
  from: 'John Doe',
  subject: 'Incredible',
  text: 'This is an incredible test message',
  to: 'johndoe@gmail.com',
})
```

Note that the options are passed to [nodemailer](https://nodemailer.com/message/). Refer to the documentation for available config options.

<!-- LICENSE/ -->
## License

Unless stated otherwise all works are:

Copyright &copy; Sebastian Landwehr <info@dword-design.de>

and licensed under:

[MIT License](https://opensource.org/licenses/MIT)
<!-- /LICENSE -->
