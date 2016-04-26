# cycle-http-server-driver

*In alpha.*

An HTTP server driver for CycleJS for managing request/response in Node.js.

## Installation

```sh
npm install cycle-http-server-driver --save
```

## Documentation

### Usage

```js
import transport from 'http'
import bunyan from 'bunyan'

import {
  makeHTTPServerDriver
} from 'cycle-http-server-driver'

const port = 8080
const logger = bunyan.createLogger({name: 'web'})

const drivers = {
  HTTPServer: makeHTTPServerDriver(port, logger, transport)
}

function main (sources) {
  return {
    HTTPServer: sources.HTTPServer.map((context) => {
      return {
        ...context,
        headers: {'Content-Type': 'text/html'},
        body: 'Hello, world!'
      }
    })
  }
}

run(main, drivers)
```
