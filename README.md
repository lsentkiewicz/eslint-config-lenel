# eslint-config-lenel

[![Build Status](https://travis-ci.org/lsentkiewicz/eslint-config-lenel.svg?branch=master)](https://travis-ci.org/lsentkiewicz/eslint-config-lenel)
[![npm version](https://badge.fury.io/js/eslint-config-lenel.svg)](https://badge.fury.io/js/eslint-config-lenel)
[![Dependencies](https://david-dm.org/lsentkiewicz/eslint-config-lenel.svg)](https://david-dm.org/lsentkiewicz/eslint-config-lenel)

An eslint config for React applications.

It contains plugins:
- [eslint-plugin-babel](https://github.com/babel/eslint-plugin-babel) - ESLint rules for babel
- [eslint-plugin-react](https://github.com/yannickcr/eslint-plugin-react) - ESLint rules for react
- [eslint-plugin-lodash](https://github.com/wix/eslint-plugin-lodash) - ESLint rules for lodash (`underscore` is forbidden)
- [eslint-plugin-import](https://github.com/benmosher/eslint-plugin-import) - ESLint plugin with rules that help validate proper imports

## Installation

```
npm install --save-dev eslint-config-lenel
```

Configure `.eslintrc`

```
{
  "extends": "eslint-config-lenel"
}
```


### Add scripts to package.json

```
"scripts": {
  "lint": "eslint --ext jsx --ext js .",
  "lint:fix": "npm run lint -- --fix"
}
```

Run scripts with `-s` flag  
```
  npm run lint -s
  npm run lint:fix -s
```

## General notes
1. Exceptions for `import/no-unresolved`  
   Eslint will report errors if you use aliases in webpack.  
   Disable it by adding:  
   ```js  

   'import/no-unresolved': [2, { ignore: ['^components/', '^containers/', '^services/', '^layouts/'] }]
   ```
2. Chai and `no-unused-expressions`
   Eslint will report errors if you use syntax: `expect(foo).to.be.true`.  
   Disable it by adding:  
   ```js  
    "no-unused-expressions": 0,
   ```
   if you have unit tests in a separate folder e.g `test/` you can create a nested config.
   Example:
   create `test/.eslintrc` and extend the base config. 
   ```js
   {
     "extends" : "../.eslintrc",
     "env"     : {
       "mocha" : true
     },
     "globals": {
       "expect": true,
     },
     "rules": {
       "no-unused-expressions": 0,
       "no-magic-numbers": 0,
     }
   }
   ```


## Contributors
* [lsentkiewicz](https://github.com/lsentkiewicz) - **Łukasz Sentkiewicz**

## License
MIT
