---
title: "Browsersync configuration"
description: "Configuring Browsersync to watch files when developing locally."
---

# Browsersync configuration

When you run the `maizzle serve` command, Maizzle uses [Browsersync](https://browsersync.io) to start a local development server and open a directory listing of your emails in your default browser.

You can then make changes to your emails, save them, and watch the browser automatically refresh the tab for you.

Maizzle sets some defaults for Browsersync, but you can customize them in your `config.js` file.

For example, here's how you'd use a custom port number:

```js [config.js]
module.exports = {
  build: {
    browsersync: {
      port: 8080,
    }
  }
}
```

These are the defaults that Maizzle uses:

### directory

Type: Boolean\
Default: `true`

When running `maizzle serve` with `directory: true`, Browsersync will open a file explorer in your default browser, showing root of the `build_local` directory.

If you set `directory: false`, the page opened by Browsersync will be blank, and you'll need to manually navigate to your emails directory.

<Alert>Use `directory: false` together with the `tunnel` option for a client demo, so they can't freely browse all of your emails by going to the root directory URL.</Alert>

### notify

Type: Boolean\
Default: `false`

Toggle Browsersync's annoying pop-over notifications. Off by default ✌

### open

Type: Boolean\
Default: `false`

Decide which URL to open automatically when Browsersync starts.

Can be `true`, `local`, `external`, `ui`, `ui-external`, `tunnel` or `false`

See [Browsersync docs](https://browsersync.io/docs/options#option-open) for details.

### port

Type: Number\
Default: `3000`

Set a custom server port number - by default, your local development server will be available at http://localhost:3000

### ui

Type: Object|Boolean\
Default: `{port: 3001}`

Browsersync includes a user interface that is accessed via a separate port, and which allows control over all devices, push sync updates and much more.

You can disable it by setting it to `false`.

### watch

Type: Array

Array of additional paths for Browsersync to watch.

By default, the following paths are watched for file changes:

- all files in your project's `src` folder
- `tailwind.config.js`
- `config.*.js`

You may define additional file and folder paths to watch when developing locally:

```js [config.js] {5,6} diff
module.exports = {
  build: {
    browsersync: {
      watch: [
+        './some/folder',
+        'some-file.js'
      ]
    }
  }
}
```

When a file in any of these watch paths is updated, Browsersync will trigger a full rebuild and changes will be reflected in the browser.
