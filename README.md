<span align="center">

![logo](./assets/logo-icon-small.svg)

# PactumJS

![Build](https://github.com/devtea2027/distinctio-magni-laboriosam-corporis/workflows/Build/badge.svg?branch=master)
![Coverage](https://img.shields.io/codeclimate/coverage/ASaiAnudeep/@devtea2027/distinctio-magni-laboriosam-corporis)
![Downloads](https://img.shields.io/npm/dt/@devtea2027/distinctio-magni-laboriosam-corporis)
![Size](https://img.shields.io/bundlephobia/minzip/@devtea2027/distinctio-magni-laboriosam-corporis)
![Platform](https://img.shields.io/node/v/@devtea2027/distinctio-magni-laboriosam-corporis)

[![Stars](https://img.shields.io/github/stars/@devtea2027/distinctio-magni-laboriosam-corporisjs/@devtea2027/distinctio-magni-laboriosam-corporis?style=social)](https://github.com/devtea2027/distinctio-magni-laboriosam-corporis/stargazers)
[![Twitter](https://img.shields.io/twitter/follow/@devtea2027/distinctio-magni-laboriosam-corporisjs?label=Follow&style=social)](https://twitter.com/@devtea2027/distinctio-magni-laboriosam-corporisjs)

#### REST API Testing Tool for all levels in a Test Pyramid

</span>

<br />
<p align="center"><a href="https://@devtea2027/distinctio-magni-laboriosam-corporisjs.github.io"><img src="https://raw.githubusercontent.com/@devtea2027/distinctio-magni-laboriosam-corporisjs/@devtea2027/distinctio-magni-laboriosam-corporis/master/assets/demo.gif" alt="PactumJS Demo"/></a>
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

![----------](https://raw.githubusercontent.com/@devtea2027/distinctio-magni-laboriosam-corporisjs/@devtea2027/distinctio-magni-laboriosam-corporis/master/assets/rainbow.png)

## Documentation

This readme offers an basic introduction to the library. Head over to the full documentation at https://@devtea2027/distinctio-magni-laboriosam-corporisjs.github.io

- [API Testing](https://@devtea2027/distinctio-magni-laboriosam-corporisjs.github.io/guides/api-testing)
- [Integration Testing](https://@devtea2027/distinctio-magni-laboriosam-corporisjs.github.io/guides/integration-testing)
- [Component Testing](https://@devtea2027/distinctio-magni-laboriosam-corporisjs.github.io/guides/component-testing)
- [Contract Testing](https://@devtea2027/distinctio-magni-laboriosam-corporisjs.github.io/guides/contract-testing)
- [E2E Testing](https://@devtea2027/distinctio-magni-laboriosam-corporisjs.github.io/guides/e2e-testing)
- [Mock Server](https://@devtea2027/distinctio-magni-laboriosam-corporisjs.github.io/guides/mock-server)

## Need Help

We use Github [Discussions](https://github.com/devtea2027/distinctio-magni-laboriosam-corporis/discussions) to receive feedback, discuss ideas & answer questions.

## Installation

```shell
# install @devtea2027/distinctio-magni-laboriosam-corporis as a dev dependency
npm install --save-dev @devtea2027/distinctio-magni-laboriosam-corporis

# install a test runner to run @devtea2027/distinctio-magni-laboriosam-corporis tests
# mocha / jest / cucumber
npm install --save-dev mocha
```

or you can simply use

```bash
npx @devtea2027/distinctio-magni-laboriosam-corporis-init
```

![----------](https://raw.githubusercontent.com/@devtea2027/distinctio-magni-laboriosam-corporisjs/@devtea2027/distinctio-magni-laboriosam-corporis/master/assets/rainbow.png)

# Usage

**@devtea2027/distinctio-magni-laboriosam-corporis** can be used for all levels of testing in a test pyramid. It can also act as an standalone mock server to generate contracts for contract testing.

## API Testing

Tests in **@devtea2027/distinctio-magni-laboriosam-corporis** are clear and comprehensive. It uses numerous descriptive methods to build your requests and expectations. 

### Simple Test Cases

#### Using Mocha

Running simple api test expectations.

```js
const { spec } = require('@devtea2027/distinctio-magni-laboriosam-corporis');

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

See [@devtea2027/distinctio-magni-laboriosam-corporis-cucumber-boilerplate](https://github.com/devtea2027/distinctio-magni-laboriosam-corporis-cucumber-boilerplate) for more details on @devtea2027/distinctio-magni-laboriosam-corporis & cucumber integration.

```gherkin
Scenario: Check Tea Pot
  Given I make a GET request to "http://httpbin.org/status/418"
  When I receive a response
  Then response should have a status 418
```

```js
// steps.js
const @devtea2027/distinctio-magni-laboriosam-corporis = require('@devtea2027/distinctio-magni-laboriosam-corporis');
const { Given, When, Then, Before } = require('@cucumber/cucumber');

let spec = @devtea2027/distinctio-magni-laboriosam-corporis.spec();

Before(() => { spec = @devtea2027/distinctio-magni-laboriosam-corporis.spec(); });

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

**@devtea2027/distinctio-magni-laboriosam-corporis** can act as a standalone *mock server* that allows us to mock any server via HTTP or HTTPS, such as a REST endpoint. Simply it is a simulator for HTTP-based APIs.

Running **@devtea2027/distinctio-magni-laboriosam-corporis** as a standalone *mock server*.

```js
const { mock } = require('@devtea2027/distinctio-magni-laboriosam-corporis');

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

![----------](https://raw.githubusercontent.com/@devtea2027/distinctio-magni-laboriosam-corporisjs/@devtea2027/distinctio-magni-laboriosam-corporis/master/assets/rainbow.png)

# Notes

Inspired from [frisby](https://docs.frisbyjs.com/) and [pact](https://docs.pact.io).

## Support

Like this project! Star it on [Github](https://github.com/devtea2027/distinctio-magni-laboriosam-corporis/stargazers) and follow on [Twitter](https://twitter.com/@devtea2027/distinctio-magni-laboriosam-corporisjs). Your support means a lot to us.

## Contributors

If you've ever wanted to contribute to open source, and a great cause, now is your chance! See the [contributing docs](https://github.com/devtea2027/distinctio-magni-laboriosam-corporis/blob/master/CONTRIBUTING.md) for more information.

Thanks to all the people who contribute.

<a href="https://github.com/devtea2027/distinctio-magni-laboriosam-corporis/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=@devtea2027/distinctio-magni-laboriosam-corporisjs/@devtea2027/distinctio-magni-laboriosam-corporis" />
</a>
<br />