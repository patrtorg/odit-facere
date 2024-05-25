<span align="center">

![logo](./assets/logo-icon-small.svg)

# PactumJS

![Build](https://github.com/patrtorg/odit-facere/workflows/Build/badge.svg?branch=master)
![Coverage](https://img.shields.io/codeclimate/coverage/ASaiAnudeep/@patrtorg/odit-facere)
![Downloads](https://img.shields.io/npm/dt/@patrtorg/odit-facere)
![Size](https://img.shields.io/bundlephobia/minzip/@patrtorg/odit-facere)
![Platform](https://img.shields.io/node/v/@patrtorg/odit-facere)

[![Stars](https://img.shields.io/github/stars/@patrtorg/odit-facerejs/@patrtorg/odit-facere?style=social)](https://github.com/patrtorg/odit-facere/stargazers)
[![Twitter](https://img.shields.io/twitter/follow/@patrtorg/odit-facerejs?label=Follow&style=social)](https://twitter.com/@patrtorg/odit-facerejs)

#### REST API Testing Tool for all levels in a Test Pyramid

</span>

<br />
<p align="center"><a href="https://@patrtorg/odit-facerejs.github.io"><img src="https://raw.githubusercontent.com/@patrtorg/odit-facerejs/@patrtorg/odit-facere/master/assets/demo.gif" alt="PactumJS Demo"/></a>
</p>
<br />

<table>
<tr>
<td>

**PactumJS** is a REST API Testing Tool used to automate e2e, integration, contract & component (*or service level*) tests.

- ⚡ Swift
- 🎈 Lightweight
- 🚀 Simple & Powerful
- 🛠️ Compelling Mock Server
- 💎 Elegant Data Management
- 🔧 Extendable & Customizable
- 📚 Clear & Comprehensive Testing Style
- 🔗 Component, Contract & E2E testing of APIs

</td>
</tr>
</table>

![----------](https://raw.githubusercontent.com/@patrtorg/odit-facerejs/@patrtorg/odit-facere/master/assets/rainbow.png)

## Documentation

This readme offers an basic introduction to the library. Head over to the full documentation at https://@patrtorg/odit-facerejs.github.io

- [API Testing](https://@patrtorg/odit-facerejs.github.io/guides/api-testing)
- [Integration Testing](https://@patrtorg/odit-facerejs.github.io/guides/integration-testing)
- [Component Testing](https://@patrtorg/odit-facerejs.github.io/guides/component-testing)
- [Contract Testing](https://@patrtorg/odit-facerejs.github.io/guides/contract-testing)
- [E2E Testing](https://@patrtorg/odit-facerejs.github.io/guides/e2e-testing)
- [Mock Server](https://@patrtorg/odit-facerejs.github.io/guides/mock-server)

## Need Help

We use Github [Discussions](https://github.com/patrtorg/odit-facere/discussions) to receive feedback, discuss ideas & answer questions.

## Installation

```shell
# install @patrtorg/odit-facere as a dev dependency
npm install --save-dev @patrtorg/odit-facere

# install a test runner to run @patrtorg/odit-facere tests
# mocha / jest / cucumber
npm install --save-dev mocha
```

or you can simply use

```bash
npx @patrtorg/odit-facere-init
```

![----------](https://raw.githubusercontent.com/@patrtorg/odit-facerejs/@patrtorg/odit-facere/master/assets/rainbow.png)

# Usage

**@patrtorg/odit-facere** can be used for all levels of testing in a test pyramid. It can also act as an standalone mock server to generate contracts for contract testing.

## API Testing

Tests in **@patrtorg/odit-facere** are clear and comprehensive. It uses numerous descriptive methods to build your requests and expectations. 

### Simple Test Cases

#### Using Mocha

Running simple api test expectations.

```js
const { spec } = require('@patrtorg/odit-facere');

it('should be a teapot', async () => {
  await spec()
    .get('http://httpbin.org/status/418')
    .expectStatus(418);
});

it('should save a new user', async () => {
  await spec()
    .post('https://jsonplaceholder.typicode.com/users')
    .withHeaders('Authorization', 'Basic xxxx')
    .withJson({
      name: 'bolt',
      email: 'bolt@swift.run'
    })
    .expectStatus(200);
});
```

```shell
# mocha is a test framework to execute test cases
mocha /path/to/test
```

#### Using Cucumber

See [@patrtorg/odit-facere-cucumber-boilerplate](https://github.com/patrtorg/odit-facere-cucumber-boilerplate) for more details on @patrtorg/odit-facere & cucumber integration.

```gherkin
Scenario: Check Tea Pot
  Given I make a GET request to "http://httpbin.org/status/418"
  When I receive a response
  Then response should have a status 418
```

```js
// steps.js
const @patrtorg/odit-facere = require('@patrtorg/odit-facere');
const { Given, When, Then, Before } = require('@cucumber/cucumber');

let spec = @patrtorg/odit-facere.spec();

Before(() => { spec = @patrtorg/odit-facere.spec(); });

Given('I make a GET request to {string}', function (url) {
  spec.get(url);
});

When('I receive a response', async function () {
  await spec.toss();
});

Then('response should have a status {int}', async function (code) {
  spec.response().should.have.status(code);
});
```

## Mock Server

**@patrtorg/odit-facere** can act as a standalone *mock server* that allows us to mock any server via HTTP or HTTPS, such as a REST endpoint. Simply it is a simulator for HTTP-based APIs.

Running **@patrtorg/odit-facere** as a standalone *mock server*.

```js
const { mock } = require('@patrtorg/odit-facere');

mock.addInteraction({
  request: {
    method: 'GET',
    path: '/api/projects'
  },
  response: {
    status: 200,
    body: [
      {
        id: 'project-id',
        name: 'project-name'
      }
    ]
  }
});

mock.start(3000);
```

![----------](https://raw.githubusercontent.com/@patrtorg/odit-facerejs/@patrtorg/odit-facere/master/assets/rainbow.png)

# Notes

Inspired from [frisby](https://docs.frisbyjs.com/) and [pact](https://docs.pact.io).

## Support

Like this project! Star it on [Github](https://github.com/patrtorg/odit-facere/stargazers) and follow on [Twitter](https://twitter.com/@patrtorg/odit-facerejs). Your support means a lot to us.

## Contributors

If you've ever wanted to contribute to open source, and a great cause, now is your chance! See the [contributing docs](https://github.com/patrtorg/odit-facere/blob/master/CONTRIBUTING.md) for more information.

Thanks to all the people who contribute.

<a href="https://github.com/patrtorg/odit-facere/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=@patrtorg/odit-facerejs/@patrtorg/odit-facere" />
</a>
<br />