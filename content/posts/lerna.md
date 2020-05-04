---
title: "Lerna"
date: 2020-05-04T14:33:12+01:00
tags: ["nodejs", "lerna", "monorepo", "docker", "expressjs"]
---

_**Monorepo** (all projects are stored in a single repository) is a relatively new concept (to me) and so I've provided more than usual hits/sample code in the kata. This is primarily to help me cement the core commands._

_The BACKGROUND to why I've created this is kata is this.  I've recently needed to create several RabbitMQ consumers through a devised pattern, including additional common functionality.  As there is common code, I did not want to violate the DRY principle so set about researching a way to do this, easily, with a `nodejs` repo. As these consumers, plus additional functionality, are small, I felt it UNNCESSARY to create a layer of complexity that would have come about if I were to have gone down the multiple repository route as well as having a private npm registry for the common code. THANKFULLY I found `Lerna` and `Lerna` fits my requirements perfectly._

## Requirements

1. Create a new `lerna` project:

```
$ mkdir lerna-kata && cd lerna-kata
$ npm i lerna
$ lerna init
```

2. Create a new package called `@kata/web`:

```
$ lerna create @kata/web -y
```

3. Add these sections into `packages/web/package.json`:

```json
  "script" : {
      "start": "node lib/web.js"
  },
  "dependencies": {    
      "express": "^4.17.1"
  }
```

4. Cut & Paste and overwrite in `packages/web/lib/web.js`:

```js
const common = require('@kata/common')
const express = require('express')
const app = express()
const router = express.Router()
const http = require('http').createServer(app)
const port = process.env.PORT || 3000
router.get('/', async (req, res) => {
    res.status(200).send(common.getMessage())
})

app.use('/', router)

http.listen(port, () => {
    console.log(`Connected, listening on port: ${port}`)
})
```

5. Create a new package called `@kata/common`:

```
$ lerna create @kata/common -y
```

6. Add these sections into packages/common.package.json:

```json
  "script" : {
      "start": "node lib/common.js"
  }
  "dependencies": {    
      "moment": "^2.25.2"
  }
```

7. Cut & Paste and overwrite in packages/common/lib/common.js

```js
const moment = require('moment')
const started = moment(Date.now())
const getMessage = () => {
    return `Web started ${moment(Date.now()).diff(started, "seconds")} seconds ago`
}
module.exports = {
    getMessage
}
```

8. Add `@kata/common` reference to `@kata/web`

9. Configure root package.json to bootstrap project dependencies

10. Configure root package.json to start all projects

11. Configure root package.json to stream logs

12. Now run 

13. Set version in all packages:

```
$ git add .
$ git commit -m "chore(release): set version"
$ lerna version --no-push --conventional-commits --no-changelog

info cli using local version of lerna
lerna notice cli v3.20.2
lerna info current version 0.0.4
lerna info Looking for changed packages since v0.0.4
lerna info getChangelogConfig Successfully resolved preset "conventional-changelog-angular"

Changes:
 - @kata/common: 0.0.4 => 0.0.5
 - @kata/web: 0.0.4 => 0.0.5

? Are you sure you want to create these versions? Yes
lerna info execute Skipping git push
lerna info execute Skipping releases
lerna success version finished
```

### Advanced 1 - scoped project

13. Start a scoped project

14. Create Dockerfile & run 

### Advanced 2 - import

15. Import existing repository

```
$ lerna import <local git repository> --dest=src
```

`src` above ^^^ must also be listed in the list of packages in the \<root>/lerna.json file:

```json
"packages": ["packages/*","src/*"]
```

## Tech

- nodejs
- lerna
- docker

## References

- [lerna](https://github.com/lerna/lerna)
- [commands](https://github.com/lerna/lerna)

## Hints

### Hint 1 - initial setup

```
$ mkdir lerna-kata && cd lerna-kata
$ npm i lerna
$ lerna init
$ lerna create @kata/web -y
$ lerna create @kata/common -y
```

### Hint 2 - bootstrap & run

To bootstrap all packages OR start, add this to \<root>/package.js:

```json
"scripts": {
    "bootstrap": "lerna clean && lerna bootstrap",
    "start": "lerna run start --stream"
}
```

### Hint 3 - add package reference

To add a reference from one project to another, run:

```
$ lerna add @kata/common --scope @kata/web
```

### Hint 4 - install dependencies

To bootstrap all dependencies, run:

```
$ cd <root>
$ npm run bootstrap
```

### Hint 5 - run

To run:

```
$ cd <root>
$ npm run start
$ curl -X GET localhost:3000
```

To access root web page:

{{< tabs "uniqueid" >}}
{{< tab "Linux" >}}

run:
```
$ curl -X GET http://localhost:3000
Web started 654 seconds ago
```
{{< /tab >}}
{{< tab "Windows" >}} 

run:
```
$ curl http://localhost:3000 -UseBasicParsing

StatusCode        : 200
StatusDescription : OK
Content           : Web started 483 seconds ago
RawContent        : HTTP/1.1 200 OK
                    Connection: keep-alive
                    Content-Length: 27
                    Content-Type: text/html; charset=utf-8
                    ETag: W/"1b-499fpsrG7b9xfw5MwAIxMn33THg"
                    X-Powered-By: Expres...
Forms             :
Headers           : {[Connection, keep-alive], [Content-Length, 27], [Content-Type, text/html; charset=utf-8], [Date, Mon, 04 May
                    2020 14:34:31 GMT]...}
Images            : {}
InputFields       : {}
Links             : {}
ParsedHtml        :
RawContentLength  : 27
```

 {{< /tab >}}
{{< /tabs >}}