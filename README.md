# The backend challenge

As a web development framework, Express has become a de facto standard, joining
the likes of Rails and Django. It's simple, fast, powerful, and makes server
development an unthinkable joy. But many Node developers fail to completely
understand the abstraction that Express provides them with.

Your challenge is this: write a micro-framework that implements the core
property of Express that is the middleware architecture. It does not have to
provide all features that Express has to offer, simply the core middleware
feature.


Take the following example server:

    var middleware = require('./middleware');

    var app = middleware.createServer();

    app.use(function (req, res, next) {
      res.write('a');
      next();
    });

    app.use('/hello', function (req, res, next) {
      res.write('b');
      next();
    });

    app.use(function (req, res, next) {
      res.write('c');
      next();
    });

    app.use('/hello', function (req, res) {
      res.end('hello');
    });

    app.use('/goodbye', function (req, res) {
      res.end('goodbye');
    });

    app.use(function (req, res) {
      res.end('end');
    });

    app.listen(3000, function () {
      console.log('Server started at 3000');
    });


Your micro-framework will implement at least 3 methods:

* `createServer()`
* `use(handler)`
* `listen(port, callback)`

The above server will run as you would expect:

* `GET /hello` would return `abchello`
* `GET /goodbye` would return `acgoodbye`
* `GET /` would return `acend`

Do you have what it takes?


## Usage

    $ npm install
    $ npm test
