# @datafire/import_run

Client library for import.io

## Installation and Usage
```bash
npm install --save @datafire/import_run
```
```js
let import_run = require('@datafire/import_run').create({
  api_key: ""
});

import_run.extractor.extractorId.cancel.post({
  "extractorId": ""
}).then(data => {
  console.log(data);
});
```

## Description



## Actions

### extractor.extractorId.cancel.post
Cancel an existing crawl.


```js
import_run.extractor.extractorId.cancel.post({
  "extractorId": ""
}, context)
```

#### Input
* input `object`
  * extractorId **required** `string`: extractorId

#### Output
* output `object`

### extractor.extractorId.start.post
Launch a crawl from an extractor that a user owns.


```js
import_run.extractor.extractorId.start.post({
  "extractorId": ""
}, context)
```

#### Input
* input `object`
  * extractorId **required** `string`: the id of the extractor to start crawling with

#### Output
* output `object`



## Definitions

### APIError
* APIError `object`
  * code `integer`: Internal error code
  * error `string`: (deprecated) A message containing a brief description of the error
  * message `string`: A message containing a brief description of the error

### CrawlRun
* CrawlRun `object`
  * extractorId `string`
  * failedUrlCount `integer`
  * guid `string`
  * rowCount `integer`
  * runtimeConfigId `string`
  * startedAt `integer`
  * state `string`
  * stoppedAt `integer`
  * successUrlCount `integer`
  * totalUrlCount `integer`
  * urlListId `string`

### Inputs
* Inputs `object`
  * Example Input `string`
  * _url **required** `string`

### ObjectStoreSearchResult
* ObjectStoreSearchResult `object`
  * hits `object`
    * hits `array`
      * items `object`
        * _id `string`
        * _score `integer`
        * _type `string`
        * fields [CrawlRun](#crawlrun)
    * total `integer`
  * timed_out `boolean`
  * took `integer`

### QueryResponse
* QueryResponse `object`
  * error `string`
  * exceptionType `string`
  * extractorData `object`
  * pageData `object`
  * runtimeConfigId `string`
  * sequenceNumber `integer`
  * timestamp `integer`
  * url `string`

### Report
* Report `object`
  * configId `string`
  * guid `string`
  * name `string`
  * published `boolean`
  * reportId `string`
  * status `string`
  * summary `object`
  * type `string`

### ReportRun
* ReportRun `object`
  * autoPublish `boolean`
  * guid `string`
  * latestConfigId `string`
  * name `string`
  * type `string`

### Schedule
* Schedule `object`
  * extractorId `string`
  * interval `string`
  * intervalData `object`
    * minutes `string`
    * time `string`
    * type `string`
  * nextRunAt `integer`
  * ownerId `string`
  * startTimestamp `integer`

### ScheduleRequest
* ScheduleRequest `object`
  * extractorId **required** `string`
  * interval **required** `string`
  * startTimestamp `integer`


