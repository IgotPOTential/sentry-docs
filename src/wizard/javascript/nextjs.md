---
name: Next.js
doc_link: https://docs.sentry.io/platforms/javascript/guides/nextjs/
support_level: production
type: framework
---

To use Sentry with your Next.js application, you will need to use Sentry’s Next.js plugin:

```bash
# Using yarn
yarn add @next/plugin-sentry @next/sentry-source-maps

# Using npm
npm install --save @next/plugin-sentry @next/sentry-source-maps
```

If you're using [Vercel](https://vercel.com) you just need to install [Sentry's Vercel integration](https://docs.sentry.io/product/integrations/vercel/) and we'll automatically configure your environment for you.

Otherwise, you'll need to configure the following environment variables:

```shell
SENTRY_DSN="___PUBLIC_DSN___"

SENTRY_RELEASE="my-application@my-application-version"

# used for sourcemap publishing
SENTRY_AUTH_TOKEN="api-auth-token"
SENTRY_PROJECT="___PROJECT_SLUG___"
SENTRY_ORG="___ORG_SLUG___"
```

Lastly, enable generation and publishing of [source maps](sourcemaps/):

```javascript
const withSourceMaps = require("@zeit/next-source-maps")();
const withSentry = require("@next/sentry-source-maps")();

module.exports = withSentry(
  withSourceMaps({
    experimental: { plugins: true },
  })
);
```
