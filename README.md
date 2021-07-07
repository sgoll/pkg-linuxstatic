# pkg-linuxstatic

Minimal reproduction that shows that builds for target platform `linuxstatic`
(e.g. `node14.17.0-linuxstatic-armv7`) complete without error but fail to run:

```
$ ./pkg-linuxstatic
pkg/prelude/bootstrap.js:1697
      throw error;
      ^

Error: Dynamic loading not supported
    at tryImporting (pkg/prelude/bootstrap.js:2028:37)
    at tryImporting (pkg/prelude/bootstrap.js:2080:16)
    at process.dlopen (pkg/prelude/bootstrap.js:2103:7)
    at Object.Module._extensions..node (internal/modules/cjs/loader.js:1144:18)
    at Module.load (internal/modules/cjs/loader.js:950:32)
    at Function.Module._load (internal/modules/cjs/loader.js:790:14)
    at Module.require (internal/modules/cjs/loader.js:974:19)
    at Module.require (pkg/prelude/bootstrap.js:1676:31)
    at require (internal/modules/cjs/helpers.js:92:18)
    at bindings (/snapshot/pkg-linuxstatic/node_modules/bindings/bindings.js:112:48)
```

Install dependencies with `yarn install`, then build package with `yarn build`.
Alternatively, use GitHub Actions and download artifact [from there](https://github.com/sgoll/pkg-linuxstatic/actions).
