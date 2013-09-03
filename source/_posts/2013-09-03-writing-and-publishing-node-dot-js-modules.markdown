---
layout: post
title: "Writing and Publishing Node.js Modules"
date: 2013-09-03 08:02
comments: true
categories: Node.js
keywords: "node.js, node.js module, modulesnode.js, publish modules node.js, write modules node.js"
description: "Writing and Publishing Node.js Modules"
---

---
<!--more-->

## Write

If you have one lib and you want share with the other programs, it's time to create a module. It's Very simple but you need known some rules.

### Structure 

{% codeblock %}

-example-module
	-lib
		example-modules.js
	-node-modules
		-example-dependencies
	-tests
	 	test-something.js
	LICENSE
	package.json
	README.md 
	
{% endcodeblock %}

#### lib
This folder contains all the files responsible for the functionality of your module.

#### node-modules
This folder contains all the dependencies(other modules) used to implementation. This is created aotumaticaly when you install some moulde.

#### tests
Contains all tests arquives tp testing your module.

#### LICENSE
Thisfile contains all informations about the license of module.

#### package.json
This is the most important file allows see all information about this module, structure, owner e etc.

{% codeblock %}
{
  "name": "example-module",
  "description": "This simple example how create a module",
  "version": "0.0.1",
  "author": {
    "name": "Example Module",
    "email": "ezample@module.com"
  },
  "keywords": [
    "example",
    "module",
    "how to"
  ],
  "contributors": [
    {
      "name": "Friend1",
      "email": "friend1@node.net"
    }
  ],
  "repository": {
    "type": "git",
    "url": "git://github.com/example-module/example-module.git"
  },
  "bugs": {
    "mail": "bugs@node.com",
    "url": "http://github.com/fb55/example-module/issues"
  },
  "directories": {
    "lib": "lib/"
  },
  "main": "lib/index.js",
  "scripts": {
    "test": "tests/test-something.js"
  },
  "dependencies": {
    "example-dependencies": "2.0"
  },
  "licenses": [
    {
      "type": "MIT",
      "url": "http://github.com/example-module/example-module/raw/master/LICENSE"
    }
  ],
  "readme": "Here you can put your readme in one string"
  "_id": "example-module@0.0.1",
  "_from": "example-module@0.0.1"
}

{% endcodeblock %}

#### README.md
This is a markdown file, contains all information how to use de module, version and example the code.

## Publish

### NPM REGISTRY
First you need go to https://npmjs.org/signup and create account and user.

### npm adduser
Now you need add user to publish your module.

{% codeblock %}
 npm adduser
 
Username: example
Password: 
Email: example@node.com
{% endcodeblock %}	

### npm publish
Now you need to go to root of your module and use this command.

{% codeblock %}
npm publish
{% endcodeblock %}

Now your module is publish congratulations!!!! 