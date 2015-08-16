# Mocha Tests + Coverage

> This page describe how to...

## Install

```bash
npm install -g istanbul
npm install mocha supertest sinon chai --save-dev
```

## Command Line


istanbul cover ./scripts/jasmine_node --captureExceptions spec/src/**/*

```bash
istanbul cover -x *.spec.js node_modules/mocha/bin/_mocha --report lcovonly --captureExceptions -- -R spec ./spec/src/**/*
# development environment
env NODE_ENV=development istanbul cover -x *.spec.js node_modules/mocha/bin/_mocha --report lcovonly -- -R spec ./spec/src/**/*
```

## Files

- [spec/src/<my_module>.spec.js](./../files/mocha_test.spec.js)

### Modules

- [Istanbul](https://github.com/gotwarlost/istanbul)
- [Mocha](https://mochajs.org)
- [Sinon](http://sinonjs.org)
- [Chai](http://chaijs.com)
- [Supertest](https://www.npmjs.com/package/supertest)