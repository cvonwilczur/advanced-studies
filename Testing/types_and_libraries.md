#Testing

Bugs cost companies a lot of money. As codebases grow, the work intended to maintain that codebase becomes more complex.

With testing, individual units of code or assets are tested to determine whether or not they work properly. Testing is one of those items that junior developers will often overlook. Every serious company will have tests, and you will be expected to write tests for your own code.

##What is a test?

A test is another file in your application that does not run in production. Instead, it's active in development, and is run before your app is pushed to production.

For example, you would write code into your terminal along the lines of:

"npm run test"

which would run through your Test Suites, confirming whether or not they have passed.

##TDD

TDD, or Test-Driven Development, means you write your tests before you write your code, and then develop to completing your tests.


##Types of Tests
Think of tests as having three main types.

###Unit Tests
Test individual functions or classes. Unit tests are easy to write, as they rely on a simple input/output. Unit tests don't test the contract, which is the interaction between two different services or functions.

Things we need include:

Scaffolding - we need a testing library. (Jasmine, Jest, Mocha)

Assertion library - provides assertion functions that allow us to test if variables contain expected values (Jasmine, Jest, Chai(usually paired with mocha))

Test runner - we need a test runner to run our tests. (jasmine, Jest, Mocha, Karma.js)

Mock Spies and Stubs - Spies provide information about the functions, while stubs replace selected functions to ensure the expected behavior happen. (Jasmine, Jest, Sinon.js)

Code Coverage - npm test -- --coverage will output a file of the coverage, which shows what percentage of your functions are covered with tests. (Istanbul, Jest)

Jasmine used to be very popular, but has since been overtaken by Jest and Mocha+Chai+Sinon.


###Integration Tests
Integration tests examine how different pieces of code work together. Compared to unit tests, you would probably use spies to observe effects between different pieces of code, or stubs and mocks to mock a database call.

Integration tests are expensive due to the dev time invested into them. They also have a lot of moving parts, which means that they'll need constant maintenance. In other words, they're brittle.

###Automation Tests
UI tests testing real-life scenarios that control the browser and ensure the expected behavior is correct. Another reference is "end-to-end" testing.

Nightwatch, Nightmare, TestCafe, cypress, etc. Automation testing tends to only be found in bigger companies where they have a budget to fund automation testing. Webdriver.io has great documentation, nightmare.js does cool stuff like web scraping.
