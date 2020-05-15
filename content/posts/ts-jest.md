---
title: "Typescript and Jest"
date: 2020-05-15T17:27:26+01:00
tags: ["nodejs", "jest", "typescript", "javascrip", "babel"]
---

A short kata to configure a nodejs project, using TypeScript instead of javascript, and to create a unit test using the Jest testing framework.

## Requirements

1. Create a new `nodejs` project and install dependencies:

```bash
$ npm init -y
$ npm i -D typescript 
    nodemon \
    jest \ 
    babel-jest \ 
    @types/jest \
    @babel/preset-typescript \
    @babel/preset-env \
    @babel/core
```

2. Initialise jest 

```bash
$ jest --init

The following questions will help Jest to create a suitable configuration for your project

√ Would you like to use Jest when running "test" script in "package.json"? ... yes
√ Choose the test environment that will be used for testing » node
√ Do you want Jest to add coverage reports? ... no
√ Automatically clear mock calls and instances between every test? ... no
```

3. Initialise typescript

```bash
$ tsc --init
message TS6071: Successfully created a tsconfig.json file.
```

4. Copy this into tsconfig.json:

```json
{
  "compilerOptions": {
    "target": "es6", 
    "module": "commonjs", 
    "sourceMap": true, 
    "outDir": "./dist", 
    "rootDir": "./src", 
    "strict": true, 
    "moduleResolution": "node", 
    "esModuleInterop": true, 
    "mapRoot": "./maps", 
    "skipLibCheck": true, 
    "forceConsistentCasingInFileNames": true 
  },
  "exclude": [
    "node_modules"
  ]
}
```

5. Configure Babel

Copy this snippet into a new file `babel.config.js`:

```js
// babel.config.js
module.exports = {
    presets: [
        [
            '@babel/preset-env',
            {
                targets: {
                    node: 'current',
                },
            },
        ],
        '@babel/preset-typescript',
    ],
};
```

6. Create your first test:

Copy this into a new file `src/index.test.js`:

```js
class Sut {
    constructor() {
    }
    getMessage = (name: string) => {
        return `Hello ${name}`
    }
}

test("given getMessage is called, when 'Garrard' is passed, then 'Hello Garrard' is returned", () => {
    // arrange
    const sut = new Sut()

    // act
    const actual = sut.getMessage("Garrard")

    // assert
    expect(actual).toEqual("Hello Garrard")
})
```

7. Now run the test

```bash
$ npm run jest

> jest1@1.0.0 test C:\source\pg\jest1
> jest

 PASS  src/index.test.ts
  √ check if task is invalid (2 ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        1.23 s
Ran all test suites.
```

## References

- [jestio](https://jestjs.io/)