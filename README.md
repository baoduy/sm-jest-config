# sm-jest-config

the sub-module of jest configuration for unit tests.

## The Sub-module path

Add this repo as the sub-module of your repo with the module path is **configs\jest**

## Recommend srciptd & npm packages

### TypeScript Project

1.  Apply the Dev Dependencies as below
    Remove the `&& codecov -t <YOUR CODECOV ID>` in the `test:ci` if you are not using CODECOV.

```json
{
  "scripts": {
    "git:jest": "git submodule update --init --remote configs/jest",
    "test":
      "npm-run-all git:jest && jest --watch --coverage --config=configs/jest/ts.jest.json",
    "test:ci":
      "npm-run-all git:jest && jest --ci --coverage --config=configs/jest/ts.jest.json && codecov -t <YOUR CODECOV ID>"
  },
  "devDependencies": {
    "@babel/cli": "latest",
    "@babel/core": "latest",
    "@babel/preset-env": "latest",
    "babel-jest": "latest",
    "babel-plugin-transform-es2015-modules-commonjs": "latest",
    "jest": "latest",
    "ts-jest": "latest",
    "npm-run-all": "latest"
  }
}
```

2.  Config the **.babelrc** file as below

```json
{
  "presets": [
    //Your presets
  ],
  "plugins": [
    //Your plugins
  ],
  "env": {
    //This for jest test
    "test": {
      "presets": ["env"],
      "plugins": ["transform-es2015-modules-commonjs"]
    }
  }
}
```

### Javascript Project

1.  Apply the Dev Dependencies as below
    Remove the `&& codecov -t <YOUR CODECOV ID>` in the `test:ci` if you are not using CODECOV.

```json
{
  "scripts": {
    "git:jest": "git submodule update --init --remote configs/jest",
    "test":
      "npm-run-all git:jest && jest --watch --coverage --config=configs/jest/jest.json",
    "test:ci":
      "npm-run-all git:jest && jest --ci --coverage --config=configs/jest/jest.json && codecov -t <YOUR CODECOV ID>"
  },
  "devDependencies": {
    "@babel/cli": "latest",
    "@babel/core": "latest",
    "@babel/preset-env": "latest",
    "babel-jest": "latest",
    "babel-plugin-transform-es2015-modules-commonjs": "latest",
    "jest": "latest",
    "npm-run-all": "latest"
  }
}
```

2.  Config the **.babelrc** file as below

```json
{
  "presets": [
    //Your presets
  ],
  "plugins": [
    //Your plugins
  ],
  //This for jest test
  "env": {
    "test": {
      "presets": ["env", "react-latest"],
      "plugins": ["transform-es2015-modules-commonjs"]
    }
    //Your other environments
  }
}
```
