# cypress-import-bug
This repo reproduces an issue between cli-plugin-e2e-cypress and cli-plugin-babel. 

The project was created by issuing `vue create` and manually selecting only babel and e2e with cypress features.

The only modification to the project is adding the following statement to the cypress test: `import Vue from 'vue'`

## Project setup
```
yarn install
```

### Reproduce bug
```
yarn test:e2e --headless
```

#### Expected behaviour
Tests pass

#### Actual behaviour
Tests fail with the following error:
```
Running: test.js...                                                                      (1 of 1) 

Oops...we found an error preparing this test file:

  ~/work/cypress-import-bug/tests/e2e/specs/test.js

The error was:


~/work/cypress-import-bug/node_modules/@babel/runtime/helpers/builtin/es6/interopRequireDefault.js:1
export default function _interopRequireDefault(obj) {
^
ParseError: 'import' and 'export' may appear only with 'sourceType: module'

This occurred while Cypress was compiling and bundling your test code. This is usually caused by:

- A missing file or dependency
- A syntax error in the file or one of its dependencies

Fix the error in your code and re-run your tests.
```
