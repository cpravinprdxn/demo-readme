# README #

## What is this repository for? ##

This repository consist test scripts for JavaScript.
Which will help people to understand how to write test scripts for JavaScript using JEST.

# Table of Contents #

* [How do I get set up?](#markdown-header-how-do-i-get-set-up)
* [Basic Folder Structure](#markdown-header-basic-folder-structure)
* [Command line Interface](#markdown-header-command-line-interface)
* [For What we writes a test script?](#markdown-header-for-what-we-writes-a-test-script)
* [Description of written test scripts](#markdown-header-description-of-written-test-scripts)
   - [Components](#markdown-header-1-components)
   * [Actions](#markdown-header-2-acions)
   * [Reducers](#markdown-header-3-reducers)
* [Some Useful things for Writing Tests](#markdown-header-some-useful-things-for-writing-tests)
   * [Shallow](#markdown-header-shallow)
   * [Enzyme](#markdown-header-enzyme)  
   * [Mount](#markdown-header-mount)
   
## How do I get set up? ##

1. Clone repository using command: **git clone https://github.com/prdxn/jest-with-javascript-unit-testing.git**

2. Extract it and inside project folder open terminal and run command: `npm install --save-dev jest`
(Which will install all required dependencies). if it shows error installing, then add `sudo` before typing above command.

**Note:** If this shows error like `/usr/bin/env: ‘node’: No such file or directory`, then open new terminal contains root directory `prdxn78@prdxn78:~$` and install  `sudo apt-get install nodejs-legacy`. Again rerun `npm test` it works properly.

3. Now you are ready to go

```
 If you want to run all test together run command: `npm test`
 If you want to run single test script run command: `npm test filename` (eg. `npm test app.test.js`)

```

## Basic Folder Structure ##
 **For writing only few tests:**
  Like if you have sum.js and want to test that `sum.test.js`, then add them on main directory
```
         -sum.js
         -sum.test.js
 ```    

**For writing many types of scripts and based on different categories:**
Like if you want to create many test for many category or projects, but for testing scripts mention `__test__` directory. In current git repo I have added folder structure for many scripts files:
```
        - testfiles/
            - projectA/
            - __test__/
                - sum.test.js
                - object.test.js
                - matchers.test.js
                - scripts/
                    - sum.js
            - projectB/
                - __test__/
                    - sum.test.js
                - scripts/
                    - sum.js
```

## For What we writes a test script? ##

Basically, we are writing unit test script to check the behavior.

for example: If there is function **sum** which takes two parameters and returns a sum of that two numbers. So in unit testing what I'll check: When I passes two numbers (2,3) to sum function it should return 5(i.e sum of that two numbers) then only this test will pass otherwise it'll fail. Same thought I utilized for writing following unit test scripts.

##Description of written test scripts
 
**Short decryption about written unit test script for JavaScript**

1. `sum.test.js`: (Repo path: `jest-with-javascript-unit-testing/`)

    Let's get started by writing a test for a hypothetical function that adds two numbers. First, create a `sum.js` file:
    
    ```
        function sum(a, b) {
          return a + b;
        }

        module.exports = sum;
    ```

    Then, create a file named `sum.test.js`. This will contain our actual test:
    
    ```
        const sum = require('./sum');
        test('adds 1 + 2 to equal 3', () => {
            expect(sum(1, 2)).toBe(3);
        });

    ```
    
    Add the following section to your `package.json`:
    
    ```
        {
          "scripts": {
            "test": "jest"
          }
        }
    ```

    Finally, run `npm test` and Jest will print this message:
    
    ```
        PASS  ./sum.test.js

        ✓ adds 1 + 2 to equal 3 (5ms)

    ```
    
2. `object.test.js`: (Repo path: `jest-with-javascript-unit-testing/testfiles/projectA/__test__/object.test.js`)

    If you want to check the value of an object, for that you have to use `toEqual`. `toEqual` recursively checks every field of an object or array, but `toBe` checks `===` equality.
    
    ```
      "use strict"

        // Object test
        test('object assignment', () => {
          const data = {one: 1};
          data['two'] = 2;
          expect(data).toEqual({one: 1, two: 2});
        });
    ```
    
    You can also test for the opposite of a matcher:
    
    ```   
        // Opposite Numbers Test
        test('adding positive numbers is not zero', () => {
          for (let a = 1; a < 10; a++) {
            for (let b = 1; b < 10; b++) {
              expect(a + b).not.toBe(0);
            }
          }
        });
    ```
 
3. `regex.test.js`: (Repo path: `jest-with-javascript-unit-testing/testfiles/projectA/__test__/regex.test.js`)
      
      In this example, we are checking strings against regular expressions with `toMatch`, we are checking for regular expression for type name. It checks alpha numeric and some special characters and also checks the characters limit.

    ```
      // Regex Matching
      var name = /^[a-zA-Z0-9$ &+, :;=^@#|'"\\\[\]. ^()%!{}-]{1,100}$/;
      test('Input type name regular expression is correct.', () => {
        var value = 'Christoph 0';
        expect(value).toMatch(name);
      });
    ```

4. `matchers.test.js`: (Repo Path: `jest-with-javascript-unit-testing/testfiles/projectA/__test__/matchers.test.js`) 

    In this test file, we have written many test scripts, If a test is failing, one of the first things to check should be whether the test is failing when it's the only test that runs. In Jest it's simple to run only one test - just temporarily change that test command to a test.only.
    

