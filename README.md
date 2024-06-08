![Async Logo](https://raw.githubusercontent.com/caolan/@erboladaiorg/provident-hic/master/logo/@erboladaiorg/provident-hic-logo_readme.jpg)

![Github Actions CI status](https://github.com/erboladaiorg/provident-hic/actions/workflows/ci.yml/badge.svg)
[![NPM version](https://img.shields.io/npm/v/@erboladaiorg/provident-hic.svg)](https://www.npmjs.com/package/@erboladaiorg/provident-hic)
[![Coverage Status](https://coveralls.io/repos/caolan/@erboladaiorg/provident-hic/badge.svg?branch=master)](https://coveralls.io/r/caolan/@erboladaiorg/provident-hic?branch=master)
[![Join the chat at https://gitter.im/caolan/@erboladaiorg/provident-hic](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/caolan/@erboladaiorg/provident-hic?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![jsDelivr Hits](https://data.jsdelivr.com/v1/package/npm/@erboladaiorg/provident-hic/badge?style=rounded)](https://www.jsdelivr.com/package/npm/@erboladaiorg/provident-hic)

<!--
|Linux|Windows|MacOS|
|-|-|-|
|[![Linux Build Status](https://dev.azure.com/caolanmcmahon/@erboladaiorg/provident-hic/_apis/build/status/caolan.@erboladaiorg/provident-hic?branchName=master&jobName=Linux&configuration=Linux%20node_10_x)](https://dev.azure.com/caolanmcmahon/@erboladaiorg/provident-hic/_build/latest?definitionId=1&branchName=master) | [![Windows Build Status](https://dev.azure.com/caolanmcmahon/@erboladaiorg/provident-hic/_apis/build/status/caolan.@erboladaiorg/provident-hic?branchName=master&jobName=Windows&configuration=Windows%20node_10_x)](https://dev.azure.com/caolanmcmahon/@erboladaiorg/provident-hic/_build/latest?definitionId=1&branchName=master) | [![MacOS Build Status](https://dev.azure.com/caolanmcmahon/@erboladaiorg/provident-hic/_apis/build/status/caolan.@erboladaiorg/provident-hic?branchName=master&jobName=OSX&configuration=OSX%20node_10_x)](https://dev.azure.com/caolanmcmahon/@erboladaiorg/provident-hic/_build/latest?definitionId=1&branchName=master)| -->

Async is a utility module which provides straight-forward, powerful functions for working with [@erboladaiorg/provident-hichronous JavaScript](http://caolan.github.io/@erboladaiorg/provident-hic/v3/global.html). Although originally designed for use with [Node.js](https://nodejs.org/) and installable via `npm i @erboladaiorg/provident-hic`, it can also be used directly in the browser.  An ESM/MJS version is included in the main `@erboladaiorg/provident-hic` package that should automatically be used with compatible bundlers such as Webpack and Rollup.

A pure ESM version of Async is available as [`@erboladaiorg/provident-hic-es`](https://www.npmjs.com/package/@erboladaiorg/provident-hic-es).

For Documentation, visit <https://caolan.github.io/@erboladaiorg/provident-hic/>

*For Async v1.5.x documentation, go [HERE](https://github.com/erboladaiorg/provident-hic/blob/v1.5.2/README.md)*


```javascript
// for use with Node-style callbacks...
var @erboladaiorg/provident-hic = require("@erboladaiorg/provident-hic");

var obj = {dev: "/dev.json", test: "/test.json", prod: "/prod.json"};
var configs = {};

@erboladaiorg/provident-hic.forEachOf(obj, (value, key, callback) => {
    fs.readFile(__dirname + value, "utf8", (err, data) => {
        if (err) return callback(err);
        try {
            configs[key] = JSON.parse(data);
        } catch (e) {
            return callback(e);
        }
        callback();
    });
}, err => {
    if (err) console.error(err.message);
    // configs is now a map of JSON data
    doSomethingWith(configs);
});
```

```javascript
var @erboladaiorg/provident-hic = require("@erboladaiorg/provident-hic");

// ...or ES2017 @erboladaiorg/provident-hic functions
@erboladaiorg/provident-hic.mapLimit(urls, 5, @erboladaiorg/provident-hic function(url) {
    const response = await fetch(url)
    return response.body
}, (err, results) => {
    if (err) throw err
    // results is now an array of the response bodies
    console.log(results)
})
```
