# hooks-prettify-linter
Tutorial on how to prettify, lint your javascript code every commit, pull, push.

## Table of content

- [Getting Started](#getting-started)
    - [Prerequisites](#built-with)
- [How to use](#how-to-use)
- [Configure CI](#configure-ci)
- [License](#license)


# Getting Started

<These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.>

## Built With

<Frameworks used>

* [Tslint](https://palantir.github.io/tslint/) 
* [Husky](https://github.com/typicode/husky) 
* [Prettier](https://github.com/prettier/prettier) 
* [Pretty-quick](https://github.com/azz/pretty-quick)

## Prerequisites

<What things you need to install the software and how to install them>
  
```
npm install prettier -D
npm install npm-run-all husky pretty-quick -D
```


# How to use

Remove formatting rules from tslint.json and let Prettier handle that.
Create a .prettierrc file:
```
{
 “printWidth”: 120,
 “singleQuote”: true,
 “useTabs”: false,
 “tabWidth”: 2,
 “semi”: true,
 “bracketSpacing”: true
}
```
For example I'm enforcing single quotes instead of double quotes.

Add the following scripts in your  package.json
```
"format:fix": "pretty-quick --staged",
"precommit": "run-s format:fix lint",
"lint": "ng lint",
```

Now, when you commit your staged files, it will first format your files and then run those through tslint. You can add prepull, prepush etc.

# Configure CI

```
"scripts: {
  "format:check": "prettier --config ./.prettierrc --list-different \"src/{app,environments,assets}/**/*{.ts,.js,.json,.css,.scss}\""
}
```

# License

MIT
