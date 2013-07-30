# StreamToMongo
Stream objects straight into a MongoDB database.

## Install
`npm install stream-to-mongo`

## Main usecase 
Seeding a database from large HTTP response or JSON file.

## Example
```
var request = require('request')
var parser = require('JSONStream').parse('rows.*.doc')
var options = { db: 'mongodb://localhost:27017/test-stream', collection: 'docs' }
var streamToMongo = require('stream-to-mongo')(options);

request('http://isaacs.couchone.com/registry/_all_docs')
  .pipe(parser)
  .pipe(streamToMongo);
```
## Test
Needs a MongoDB instance running.
`make test`
