# TypeScript React Relay Demo

## Steps to reproduce:
1) Run `yarn` to install dependencies
2) Run `yarn tsc`, which shows an error with the following import:
```
src/index.ts:1:35 - error TS7016: Could not find a declaration file for module 'react-relay/lib/relay-hooks/ProfilerContext'. '~/ts-react-relay/node_modules/react-relay/lib/relay-hooks/ProfilerContext.js' implicitly has an 'any' type.
  If the 'react-relay' package actually exposes this module, consider sending a pull request to amend 'https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/react-relay'

1 import ProfilerContextActual from 'react-relay/lib/relay-hooks/ProfilerContext';
                                    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Found 1 error in src/index.ts:1
```
3) Run `yarn build` to compile the code with babel
4) Run `yarn start` to run the built file with node, and you will see an error similar to the following:
```
$ node dist/index.js
node:internal/modules/cjs/loader:936
  throw err;
  ^

Error: Cannot find module 'react-relay/relay-hooks/ProfilerContext'
Require stack:
- ~/ts-react-relay/dist/index.js
    at Function.Module._resolveFilename (node:internal/modules/cjs/loader:933:15)
    at Function.Module._load (node:internal/modules/cjs/loader:778:27)
    at Module.require (node:internal/modules/cjs/loader:1005:19)
    at require (node:internal/modules/cjs/helpers:102:18)
    at Object.<anonymous> (~/ts-react-relay/dist/index.js:5:48)
    at Module._compile (node:internal/modules/cjs/loader:1105:14)
    at Object.Module._extensions..js (node:internal/modules/cjs/loader:1159:10)
    at Module.load (node:internal/modules/cjs/loader:981:32)
    at Function.Module._load (node:internal/modules/cjs/loader:822:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:77:12) {
  code: 'MODULE_NOT_FOUND',
  requireStack: [ '~/ts-react-relay/dist/index.js' ]
}
error Command failed with exit code 1.
```

## Optional steps to verify with `tsc` (versus babel):
0) Run `yarn` to install dependencies
1) Run `yarn build-tsc` to compile the code with tsc
2) Run `yarn start` to run the built file with node, and you will see an error similar to the following:
```$ node dist/index.js
node:internal/modules/cjs/loader:936
  throw err;
  ^

Error: Cannot find module 'react-relay/relay-hooks/ProfilerContext'
Require stack:
- ~/ts-react-relay/dist/index.js
    at Function.Module._resolveFilename (node:internal/modules/cjs/loader:933:15)
    at Function.Module._load (node:internal/modules/cjs/loader:778:27)
    at Module.require (node:internal/modules/cjs/loader:1005:19)
    at require (node:internal/modules/cjs/helpers:102:18)
    at Object.<anonymous> (~/ts-react-relay/dist/index.js:7:43)
    at Module._compile (node:internal/modules/cjs/loader:1105:14)
    at Object.Module._extensions..js (node:internal/modules/cjs/loader:1159:10)
    at Module.load (node:internal/modules/cjs/loader:981:32)
    at Function.Module._load (node:internal/modules/cjs/loader:822:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:77:12) {
  code: 'MODULE_NOT_FOUND',
  requireStack: [ '~/ts-react-relay/dist/index.js' ]
}
error Command failed with exit code 1.
```