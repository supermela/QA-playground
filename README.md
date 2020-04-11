# QA-playground

Cucumber JS Script - Create a new test and installing dependencies

Open terminal

```mkdir name-folder-test```
```cd name-folder-test```
```npm  init```

``` This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (cucumber-test1) ls
version: (1.0.0) 
description: 
entry point: (index.js) 
test command: 
git repository: 
keywords: 
author: melania
license: (ISC) 
About to write to /Users/mela/cucumber-test1/package.json:

{
  "name": "ls",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "melania",
  "license": "ISC"
}


Is this OK? (yes) yes
mela@melanias-air cucumber-test1 % ```

Open VS code
Open the folder just created
In the folder:
you need to create .babelrc file with the following configuration:

```
{
    "presets": [
      [
        "@babel/preset-env",
        {
          "targets": {
            "node": "current"
          }
        }
      ]
    ]
  }
```

You  need to install babel.

Open the terminal in VC and:

``` npm install @babel/polyfill @babel/cli @babel/core @babel/preset-env @babel/register --save-dev ```

Install WebDriverIO in this folder, as well as a WebDriverIO CLI (the test runner)
``` npm i webdriverio @wdio/cli```
Then, run
``` ./node_modules/.bin/wdio config```
into the file 
Wido.conf.js

change the browser option here (in the Capabilities section) to Chrome, so my test will run in Chrome — ```browserName: "chrome"```
In the Test Configurations section, I changed the log level to warn, so I only see the warnings or errors in the console — ```logLevel: "warn"```
in the Hooks section, I'm going to uncomment the beforeSession function so I can load Babel.
I will add the following code to require Babel.
``` beforeSession: function(config, capabilities, specs) {
    require("@babel/register");}```

Scroll down to the cucumberOpts object. Change the property require it to:
``` require: [
    "./steps/**/given.js",
    "./steps/**/when.js",
    "./steps/**/then.js"
], // <string[]> (file/dir) require files before executing features ```
Create a folder “steps” in the root of the project and files named “given.js” “when.js” “then.js”



In the exports.config = {} 
If you work with chrome you have to add 
path:’/’ 


If you want to add the script to run the test you can add It on package.json inside script 

"testCucumber": "./node_modules/.bin/wdio ./wdio.conf.js"

If you want run it you have to type on the terminal:

npm run testCucumber