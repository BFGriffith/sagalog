# **SAGALOG**
> “a Campaign Management System for tabletop role-playing games built by a gamer for gamers, with the goal of helping Dungeon/Game Masters and players conveniently archive and get the most out of their tabletop-RPG experiences!”

---
## STACK:

* Persistence store: [MongoDB](http://www.mongodb.org/) hosted on [MongoLab](https://mongolab.com/)
* BACK-END: [Node.js](http://nodejs.org/)
* [AngularJS](http://www.angularjs.org/) on the client-side
* CSS based on [Twitter's bootstrap](http://getbootstrap.com/)

### BUILD:

* focused on AngularJS and tightly integrated with other tools commonly used in the AngularJS community:
* powered by [Grunt.js](http://gruntjs.com/)
* testing using [Jasmine](http://jasmine.github.io/) syntax
* tests executed by [Karma Test Runner](http://karma-runner.github.io/0.8/index.html) (integrated with the Grunt.js build)
* build supports JS, CSS and AngularJS templates minification
* [Twitter's bootstrap](http://getbootstrap.com/) with LESS templates processing integrated into the build
* [Travis-CI](https://travis-ci.org/) integration

---
## DEVELOPMENT:

### Folder-Structure:
At the top level, the repository is split into a client folder and a server folder.  The client folder contains the client-side AngularJS code. The server folder contains a very basic Express based webserver that delivers and supports the application.
Structure in the client folder is as follows:
* `node_modules` contains build tasks for [Grunt](http://gruntjs.com/) along with other Node packages
* `dist` contains build results
* `src` contains application's sources
* `test` contains test sources, configuration, and dependencies
* `vendor` contains external dependencies for the application

### Default Build:
The default `grunt` task will build (check the JavaScript [lint], run the unit tests (test:unit) and build distributable files) and run all unit tests: `grunt` (or `grunt.cmd` on Windows). The tests are run by karma and need one or more browsers open to actually run the tests.
* `cd client`
* `grunt`
* Open one or more browsers and point them to [http://localhost:8080/__test/]. Once the browsers connect, the tests will run and the build will complete.
* While the browsers are left open at this url, subsequent runs of `grunt` will automatically run the tests against these browsers.

### Continuous Building:
The “watch” grunt task will monitor the source files and run the default build task every time a file changes: `grunt watch`.

### Build without Tests:
Run the build task: `grunt build`.

### Building “release” code:
Build a release version of the app, with minified files; this task will also run the “end to end” (e2e) tests.
The e2e tests require the server to be started and also one or more browsers open to run the tests (the same browsers as for the unit tests).
* `cd client`
* Run `grunt release`
* Open one or more browsers and point them to [http://localhost:8080/__test/]. Once the browsers connect the tests will run and the build will complete.
* While the browsers are left open at this url, subsequent runs of `grunt` will automatically run the tests against these browsers.

### Continuous Testing:
Grunt (karma) will continuously watch for file changes and automatically run all the tests on every change, without rebuilding the distribution files. This can make the tests run faster when doing test driven development without needing to actually run the application itself.
* `cd client`
* Run `grunt test-watch`.
* Open one or more browsers and point them to [http://localhost:8080/__test/].
* Each time a file changes, the tests will be run against each browser.