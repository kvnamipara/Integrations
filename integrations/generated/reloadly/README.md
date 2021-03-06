# @datafire/reloadly

Client library for Reloadly REST APIs

## Installation and Usage
```bash
npm install --save @datafire/reloadly
```
```js
let reloadly = require('@datafire/reloadly').create();

reloadly.topups.post({}).then(data => {
  console.log(data);
});
```

## Description

The Reloadly APIs are HTTP-based RESTful APIs that use OAuth 2.0 for authorization. API request and response bodies are formatted in JSON.

## GET STARTED

### Authentication & Authorization

-----------------

The Reloadly REST API uses the OAuth 2.0 protocol to authorize calls. OAuth is an open standard that many companies use to provide secure access to protected resources.

When you create a developer account. Reloadly generates a set of OAuth client ID and secret credentials for your app for both sandbox and live environments. You pass these credentials in the `Authorization` header in the get access token request.

In exchange for these credentials, the Reloadly authorization server issues access tokens called bearer tokens that you use for authorization when you make REST API requests. A bearer token enables you to complete actions on behalf of, and with the approval of the resource owner.

The `access_token` field in the get access token response contains a bearer token, indicated by the `token_type` of `Bearer` :

+ Response 200 (application/json)

        {
            "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImtpZCI6Ik0wWXpRa",
            "scope": "<scopes>",
            "expires_in": "5184000",
            "token_type": "Bearer"
        }

Include this bearer token in API requests in the `Authorization` header with the `Bearer` authentication scheme.

This sample request uses a bearer token to list topup transactions for an user account :

```curl
curl -v -X GET https://topups-sandbox.reloadly.com/transactions?page=1&size=3 \
    -H "Accept: application/com.reloadly.topups-v1+json" \
    -H "Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImtpZCI6Ik0wWXpRa" \
```

Access tokens have a finite lifetime. The `expires_in` field in the <a href="#get-access-token-response">get access token response</a> indicates the lifetime, in seconds, of the access token.
For example, an expiry value of 3600 indicates that the access token expires in one hour from the time the response was generated.

To detect when an access token expires, write code to either :

+ Keep track of the `expires_in` value in the token response. The value is expressed in seconds.

+ Handle the HTTP `401 Unauthorized` status code and the `TOKEN_EXPIRED` error code in the <a href="#error-response-message">error response message</a>. The API endpoint issues this status code when it detects an expired token.

Before you create another token, re-use the access token until it expires. See the <a href="#rate-limiting-guideline">rate limiting guidelines.</a>

### API Requests ###

-----------------

To construct a REST API request, combine these components : <br /><br />

###### Component &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Description ######

<table>
<tbody>
<tr>
<td><p>The HTTP method</p></td>
<td><ul><li><code>GET</code>. Requests data from a resource.</li><li><code>POST</code>. Submits data to a resource to process.</li><li><code>PUT</code>. Updates a resource.</li><li><code>PATCH</code>. Partially updates a resource.</li><li><code>DELETE</code>. Deletes a resource.</li></ul></td>
</tr>
<tr>
<td><p>The&nbsp;URL&nbsp;to&nbsp;the&nbsp;API&nbsp;service</p></td>
<td><ul><li>Sandbox. <code>https://topups-sandbox.reloadly.com</code></li><li>Live. <code>https://topups.reloadly.com</code></li></ul></td>
</tr>
<tr>
<td><p>The URI to the resource</p></td>
<td>The resource to query, submit data to, update, or delete. For example, <code>/reports/transactions</code>.</td>
</tr>
<tr>
<td><p><a href="#query-parameters" pa-marked="1">Query parameters</a></p></td>
<td>Optional. Controls which data appears in the response. Use to filter, limit the size of, and sort the data in an API response.</td>
</tr>
<tr>
<td><p><a href="#http-request-headers" pa-marked="1">HTTP request headers</a></p></td>
<td>Includes the <code>Authorization</code> header with the access token.</td>
</tr>
<tr>
<td><p>A JSON request body</p></td>
<td>Required for most <code>GET</code>, <code>POST</code>, <code>PUT</code>, and <code>PATCH</code> calls.</td>
</tr>
</tbody>
</table>

### &nbsp;&nbsp;Query Parameters

For most REST `GET` calls, you can specify one or more optional query parameters on the request URI to filter, limit the size of, and sort the data in an API response. For filter parameters, see the individual `GET` calls.<br /><br />

To limit, or <em>page</em>, and sort the data that is returned in some API responses, use these, or similar, query parameters :

> **Note** : Not all pagination parameters are available for all APIs.<br />
<table>
<thead>
<tr>
<th>Parameter</th>
<th>Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>count</code></td>
<td>integer</td>
<td>The number of items to list in the response.</td>
</tr>
<tr>
<td><code>startTime</code></td>
<td>integer</td>
<td>The start date and time for the range to show in the response, in <a href="https://tools.ietf.org/html/rfc3339#section-5.6" class="dx-external-link" title="external link" target="_blank" rel="noopener noreferrer" pa-marked="1">Internet date and time format</a>.<a href="https://www.iso.org/iso-8601-date-and-time-format.html" target="_blank"> (ISO 8601)</a> For example, <code>startTime=2018-03-06 00:00:00</code>.</td>
</tr>
<tr>
<td><code>endTime</code></td>
<td>integer</td>
<td>The end date and time for the range to show in the response, in <a href="https://tools.ietf.org/html/rfc3339#section-5.6" class="dx-external-link" title="external link" target="_blank" rel="noopener noreferrer" pa-marked="1">Internet date and time format</a>.<a href="https://www.iso.org/iso-8601-date-and-time-format.html" target="_blank"> (ISO 8601)</a> For example, <code>endTime=2016-03-06 23:59:59</code>.</td>
</tr>
<tr>
<td><code>page</code></td>
<td>integer</td>
<td>The zero-relative start index of the entire list of items that are returned in the response. So, the combination of <code>page=0</code> and <code>page_size=20</code> returns the first 20 items. The combination of <code>page=20</code> and <code>page_size=20</code> returns the next 20 items.</td>
</tr>
<tr>
<td><code>size</code></td>
<td>integer</td>
<td>The number of items to return in the response.</td>
</tr>
<tr>
<td><code>sortBy</code></td>
<td>string</td>
<td>Sorts the transactions in the response by a specified value, such as the create time or update time.</td>
</tr>
<tr>
<td><code>sortOrder</code></td>
<td>string</td>
<td>Sorts the items in the response in ascending or descending order.</td>
</tr>
</tbody>
</table>

###

-------------------------

For example, the Invoicing API returns details for four invoices beginning with the third invoice and includes the total count of invoices in the response:<br />

```curl
curl -v -X GET https://sandbox.topups.reloadly.com/transactions?page=1&size=10&startTime=2018-03-01 00:00:00&endTime=2018-03-31 23:59:59 \
    -H "Accept: application/com.reloadly.topups-v1+json" \
    -H "Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImtpZCI6Ik0wWXpRa" \
```

<br />

### &nbsp;&nbsp;Request Headers

The commonly used HTTP request headers are : <br />

<table>
    <colgroup><col width="33%">
    <col width="67%">
    </colgroup><thead>
        <tr>
            <th>Header</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td id="accept"><strong>Accept</strong></td>
            <td>
                <p>Required for operations with a response body.</p>
                <p>Specifies the response format. The syntax is:</p>
                <pre class="dx-pre-hljs"><code class="hljs">Accept: application/<var>format</var></code></pre>
                <p>Where <code><var>format</var></code> is <code><strong>com.reloadly.topups-v1+json</strong></code>.</p>
            </td>
        </tr>
        <tr>
            <td id="authorization"><strong>Authorization</strong></td>
            <td>
                <p>Required to get an access token or make API calls.</p>
                <p>To <a href="/docs/api/overview/#get-an-access-token" pa-marked="1">get an access token</a>, set this header to your <code>client_id</code> and <code>secret</code> credentials.</p>
                <blockquote class="dx-blockquote-note"><strong>Note:</strong> If you use cURL, specify <code>-u "client_id:secret"</code>.</blockquote>
                <p>To make REST API calls, include the bearer token in the <code>Authorization</code> header with the <code>Bearer</code> authentication scheme:</p>
                <pre class="dx-pre-hljs"><code class="hljs">Authorization: Bearer <var>Access-Token</var></code></pre>
            </td>
        </tr>
        <tr>
            <td id="content-type"><strong>Content-Type</strong></td>
            <td>
                <p>Required for operations with a request body.</p>
                <p>Specifies the request format. The syntax is:</p>
                <pre class="dx-pre-hljs"><code class="hljs">Content-Type: application/<var>format</var></code></pre>
                <p>Where <code><var>format</var></code> is <code>json</code>.</p>
            </td>
        </tr>
    </tbody>
</table>

### API Responses ###

-----------------

Reloadly API calls return HTTP status codes. Some API calls also return JSON response bodies that include information about the resource including one or more contextual HATEOAS links. Use these links to request more information about and construct an API flow that is relative to a specific request.

###&nbsp;&nbsp; HTTP status codes

Each REST API request returns a <strong><a href="#success">success</a></strong> or <strong><a href="#error">error</a></strong> status code.

#### Success

<table>
<thead>
<tr>
<th style="text-align:left">Status code</th>
<th style="text-align:left">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left"><code>200 OK</code></td>
<td style="text-align:left">The request succeeded.</td>
</tr>
<tr>
<td style="text-align:left"><code>201 Created</code></td>
<td style="text-align:left">A <code>POST</code> method successfully created a resource. If the resource was already created by a previous execution of the same method, for example, the server returns the HTTP <code>200 OK</code> status code.</td>
</tr>
<tr>
<td style="text-align:left"><code>202 Accepted</code></td>
<td style="text-align:left">The server accepted the request and will execute it later.</td>
</tr>
<tr>
<td style="text-align:left"><code>204 No Content</code></td>
<td style="text-align:left">The server successfully executed the method but returns no response body.</td>
</tr>
</tbody>
</table>

---------------------------

#### Error

In the responses for failed requests, Reloadly returns HTTP <strong>`4XX`</strong> or <strong>`5XX`</strong> status codes.<br /><br />

For all errors except Identity errors, Reloadly returns an error response body that includes additional error details in this format:

```
{
  "timeStamp": ERROR_TIME_STAMP (numerical),
  "message": "Account verification failed, invalid or expired token",
  "infoLink": "ERROR_DOCUMENTATION_LINK",
  "path": "/accounts/verify",
  "errorCode": "ERROR_CODE",

  // Some types of errors also include a details array:
  "details": [
    {
        "field": "FIELD_NAME",
        "issue": "PROBLEM_WITH_FIELD"
    }
  ]
}
```

In the responses, Reloadly returns these HTTP status codes for failed requests:

<table>
<thead>
<tr>
<th style="text-align:left">HTTP&nbsp;status&nbsp;code</th>
<th style="text-align:left">Typical error&nbsp;code and error&nbsp;message</th>
<th style="text-align:left">Cause</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left"><code>400 Bad Request</code></td>
<td style="text-align:left"><code>INVALID_REQUEST</code>. Request is not well-formed, syntactically incorrect, or violates schema.</td>
<td style="text-align:left">See <a href="#validation-errors" pa-marked="1">Validation errors</a>. The server could not understand the request. Indicates one of these conditions:<ul><li>The API cannot convert the payload data to the underlying data type.</li><li>The data is not in the expected data format.</li><li>A required field is not available.</li><li>A simple data validation error occurred.</li></ul></td>
</tr>
<tr>
<td style="text-align:left"><code>401 Unauthorized</code></td>
<td style="text-align:left"><code>AUTHENTICATION_FAILURE</code>. Authentication failed due to invalid authentication credentials.</td>
<td style="text-align:left">See <a href="#authentication-errors" pa-marked="1">Authentication errors</a>. The request requires authentication and the caller did not provide valid credentials.</td>
</tr>
<tr>
<td style="text-align:left"><code>403 Forbidden</code></td>
<td style="text-align:left"><code>NOT_AUTHORIZED</code>. Authorization failed due to insufficient permissions.</td>
<td style="text-align:left">The client is not authorized to access this resource although it might have valid credentials. For example, the client does not have the correct OAuth 2 scope. Additionally, a business-level authorization error might have occurred. For example, the account holder does not have sufficient funds.</td>
</tr>
<tr>
<td style="text-align:left"><code>404 Not Found</code></td>
<td style="text-align:left"><code>RESOURCE_NOT_FOUND</code>. The specified resource does not exist.</td>
<td style="text-align:left">The server did not find anything that matches the request URI. Either the URI is incorrect or the resource is not available. For example, no data exists in the database at that key.</td>
</tr>
<tr>
<td style="text-align:left"><code>405 Method Not Allowed</code></td>
<td style="text-align:left"><code>METHOD_NOT_SUPPORTED</code>. The server does not implement the requested HTTP method.</td>
<td style="text-align:left">The service does not support the requested HTTP method. For example, <code>PATCH</code>.</td>
</tr>
<tr>
<td style="text-align:left"><code>406 Not Acceptable</code></td>
<td style="text-align:left"><code>MEDIA_TYPE_NOT_ACCEPTABLE</code>. The server does not implement the media type that would be acceptable to the client.</td>
<td style="text-align:left">The server cannot use the client-request media type to return the response payload. For example, this error occurs if the client sends an <code>Accept: application/xml</code> request header but the API can generate only an <code>application/json</code> response.</td>
</tr>
<tr>
<td style="text-align:left"><code>415</code>&nbsp;<code>Unsupported</code>&nbsp;<code>Media</code>&nbsp;<code>Type</code></td>
<td style="text-align:left"><code>UNSUPPORTED_MEDIA_TYPE</code>. The server does not support the request payload’s media type.</td>
<td style="text-align:left">The API cannot process the media type of the request payload. For example, this error occurs if the client sends a <code>Content-Type: application/xml</code> request header but the API can only accept <code>application/json</code> request payloads.</td>
</tr>
<tr>
<td style="text-align:left"><code>422 Unprocessable Entity</code></td>
<td style="text-align:left"><code>UNPROCCESSABLE_ENTITY</code>. The API cannot complete the requested action, or the request action is semantically incorrect or fails business validation.</td>
<td style="text-align:left">The API cannot complete the requested action and might require interaction with APIs or processes outside of the current request. No systemic problems limit the API from completing the request. For example, this error occurs for any business validation errors, including errors that are not usually of the <code>400</code> type.</td>
</tr>
<tr>
<td style="text-align:left"><code>429 Unprocessable Entity</code></td>
<td style="text-align:left"><code>RATE_LIMIT_REACHED</code>. Too many requests. Blocked due to rate limiting.</td>
<td style="text-align:left">The rate limit for the user, application, or token exceeds a predefined value. See <a href="https://tools.ietf.org/html/rfc6585" class="dx-external-link" title="external link" target="_blank" rel="noopener noreferrer" pa-marked="1">RFC 6585</a>.</td>
</tr>
<tr>
<td style="text-align:left"><code>500 Internal Server Error</code></td>
<td style="text-align:left"><code>INTERNAL_SERVER_ERROR</code>. An internal server error has occurred.</td>
<td style="text-align:left">A system or application error occurred. Although the client appears to provide a correct request, something unexpected occurred on the server.</td>
</tr>
<tr>
<td style="text-align:left"><code>503 Service Unavailable</code></td>
<td style="text-align:left"><code>SERVICE_UNAVAILABLE</code>. Service Unavailable.</td>
<td style="text-align:left">The server cannot handle the request for a service due to temporary maintenance.</td>
</tr>
</tbody>
</table>

----------------------

<h4 id="validation-errors">Validation errors</h4>

For validation errors, Reloadly returns the HTTP `400 Bad Request` status code.<br /><br />

To prevent validation errors, ensure that parameters are of the right type and conform to these constraints:<br /><br />

<table>
<thead>
<tr>
<th style="text-align:left">Parameter&nbsp;type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left">Character</td>
<td>Names, addresses, phone numbers, and so on have maximum character limits.</td>
</tr>
<tr>
<td style="text-align:left">Numeric</td>
<td>Amounts, ids, and so on must use non-negative numeric values and have required formats. For example, a CVV must be three or four numbers while a credit card number must contain only numbers.</td>
</tr>
<tr>
<td style="text-align:left">Required</td>
<td>Must be included in the request. For example, when you provide credit card information, you must include a postal code for most countries.</td>
</tr>
<tr>
<td style="text-align:left">Monetary</td>
<td>Must use the right currency.</td>
</tr>
</tbody>
</table>

---------------------

<h4 id="authentication-errors">Authentication errors</h4>

For authentication errors, Reloadly returns the HTTP `401 Unauthorized` status code. See authentication and authorization.<br /><br />
Access token-related issues often cause authentication errors.<br /><br />
Ensure that the access token is valid and present and not expired.

###&nbsp;&nbsp; HATEOAS links

Hypermedia as the Engine of Application State (HATEOAS) is a constraint of the REST application architecture that distinguishes it from other network application architectures.<br /><br />
This excerpt from a sample response shows an array of HATEOAS links:<br /><br />

```
{
  "links": [{
    "href": "https://api.reloadly.com/payments/4",
    "rel": "self",
    "method": "GET"
  }, {
    "href": "https://api.reloadly.com/payments/4/refund",
    "rel": "refund",
    "method": "POST"
  }]
}
```

You can use the links in this example, as follow :

- Use the <strong>`self`</strong> link to get more information about the request. Combine the method and the target URL to make the call :
    ```
    GET https://api.reloadly.com/payments/4
    ```

- Use the <strong>`refund`</strong> link to request a refund :
    ```
    POST https://api.reloadly.com/payments/4/refund
    ```

The elements in the <strong>`link`</strong> object are :<br />

<table>
<thead>
<tr>
<th>Element</th>
<th>Required</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="#the-href-element" pa-marked="1"><code>href</code></a></td>
<td>Required</td>
<td>The target URL.</td>
</tr>
<tr>
<td><a href="#the-rel-element" pa-marked="1"><code>rel</code></a></td>
<td>Required</td>
<td>The link relationship type.</td>
</tr>
<tr>
<td><a href="#the-method-element" pa-marked="1"><code>method</code></a></td>
<td>Optional</td>
<td>The HTTP method. Default is <code>GET</code>.</td>
</tr>
</tbody>
</table>

#### The href element

The <strong>`href`</strong> element contains the complete target URL, or link, to use in combination with the HTTP <strong>`method`</strong> to make the related call. <strong>`href`</strong> is the key HATEOAS component that links a completed call with a subsequent call.
<br />

#### The rel element

The <strong>`rel`</strong> element contains the link relationship type, or how the href link relates to the previous call.
<br />

<p>For a complete list of the link relationship types, see <a href="https://www.iana.org/assignments/link-relations/link-relations.xhtml#link-relations-1" class="dx-external-link" title="external link" target="_blank" rel="noopener noreferrer" pa-marked="1">Link Relationship Types</a>.</p>

<br />

#### The method element

Optional. The <strong>`method`</strong> element contains an HTTP method. If present, use this method to make a request to the target URL. If absent, the default method is <strong>`GET`</strong>.
<br /><br /><br />
The HTTP methods are :<br />

<table>
<thead>
<tr>
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>DELETE</code></td>
<td>Deletes a resource.</td>
</tr>
<tr>
<td><code>GET</code></td>
<td>Shows details for a resource or lists resources.</td>
</tr>
<tr>
<td><code>PATCH</code></td>
<td>Partially updates a resource.</td>
</tr>
<tr>
<td><code>POST</code></td>
<td>Creates or manages a resource.</td>
</tr>
<tr>
<td><code>PUT</code></td>
<td>Updates a resource.</td>
</tr>
</tbody>
</table>

<br /><br />

### Make Your First Call ###

-----------------

<br />
To make REST API calls, create a Reloadly developer account and get an access token : <br /><br />

<table>
<thead>
<tr>
<th></th>
<th></th>
</tr>
</thead>
<tbody>
<tr>
<td>1.</td>
<td><a href="https://reloadly-dev.herokuapp.com" target="_blank" pa-marked="1"><strong>Create a developer account</strong></a>.<br>When you create a developer account, Reloadly generates a set of OAuth credentials.</td>
</tr>
<tr>
<td>2.</td>
<td><a href="#get-an-access-token" pa-marked="1"><strong>Get an access token</strong></a>.<br>Pass the OAuth credentials in a get access token call.<br>In response, the Reloadly authorization server issues an access token.</td>
</tr>
<tr>
<td>3.</td>
<td><a href="#make-rest-api-calls" pa-marked="1"><strong>Make REST API calls</strong></a>.<br>Use the access token for authentication when you make REST API calls.</td>
</tr>
</tbody>
</table>

<br />

#### Get an access token

<blockquote class="dx-blockquote-tip">
<p><strong>URLs:</strong></p>
<ul>
<li>Live : <strong>`https://reloadly.auth0.com/oauth/token`</strong></li>
<li>Sandbox : <strong>`https://reloadly-sandbox.auth0.com/oauth/token`</strong></li>
</ul>
</blockquote><br />

<p>To get an access token, you pass your OAuth credentials in a get access token call. To make this call, you can use either cURL on the command line or the Postman app.</p><br />

<p>In response, the Reloadly authorization server issues an access token.</p><br />

<p>Re-use the access token until it expires. See our rate limiting guidelines. When it expires, you can get a new token.</p>

#### cURL example

<blockquote class="dx-blockquote-tip">
<p><strong>Tips:</strong></p>
<ul>
<li>If you use Windows, use a Bash shell to make cURL calls.</li>
<li>If you use a command-line tool other than cURL, set <code>content-type</code> to <code>application/json</code>.</li>
</ul>
</blockquote><br />

<strong>1.</strong> Download <a href="https://curl.haxx.se/download.html" target="_blank">cURL</a> for your environment.
<br /><br />
<strong>2.</strong> From the command line, run this command :<br /><br />

```
curl -d '{
            "client_id":"YOUR_CLIENT_ID",
            "client_secret":"YOUR_CLIENT_SECRET",
            "grant_type":"client_credentials",
            "audience":"https://topups.reloadly.com"
        }' \
    -H "Content-Type: application/json" \
    -X POST https://reloadly.auth0.com/oauth/token \
```
<br />
Where : <br />
<table>
    <colgroup><col width="25%">
    <col width="75%">
    </colgroup><tbody><tr>
       <td><code>https://reloadly.auth0.com/oauth/token</code></td>
       <td>The get access token endpoint.</td>
    </tr>
    <tr>
       <td>
          <code><var>client_id</var></code>
       </td>
       <td>Your client ID.</td>
    </tr>
    <tr>
       <td>
          <code><var>secret</var></code>
       </td>
       <td>Your client secret.</td>
    </tr>
    <tr>
       <td>
          <code><var>audience</var></code>
       </td>
       <td>The API you're requesting the access token for. Example <code>https://topups.reloadly.com</code></td>
    </tr>
    <tr>
       <td><code>grant_type</code></td>
       <td>The grant type. Set to <code>client_credentials</code>.</td>
    </tr>
 </tbody></table>
<br />

<strong>3.</strong> View the <a href="#sample-response">sample response</a>.<br /><br />

#### Postman example
<ol>
   <li>
      <p>Download the latest version of <a href="https://www.getpostman.com/" class="dx-external-link" title="external link" target="_blank" rel="noopener noreferrer" pa-marked="1">Postman</a> for your environment, and open Postman.</p>
   </li>
   <li>
       <p>Select the <code>POST</code> method.</p>
   </li>
   <li>
       <p>Enter the <code>https://reloadly.auth0.com/oauth/token</code> request URL for LIVE mode.</p>
       OR
       <p>Enter the <code>https://reloadly-sandbox.auth0.com/oauth/token</code> request URL for SANDBOX (Test) mode.</p>
   </li>
   <li>
      <p>On the <strong>Header</strong> tab, enter <strong>Content-Type</strong> under key and <strong>application/json</strong> as value : </p>
      <table>
        <colgroup><col width="25%">
        <col width="75%">
         </colgroup><tbody><tr>
            <td><strong>key</strong></td>
            <td>Content-Type</td>
         </tr>
         <tr>
            <td><strong>value</strong></td>
            <td>application/json</td>
         </tr>
      </tbody></table>
   </li>
   <li>
      <p>On the <strong>Body</strong> tab, select <strong>raw</strong> and enter this information : </p>
    <code>
      {

       "client_id": "YOUR_CLIENT_ID",

       "client_secret": "YOUR_CLIENT_SECRET",

       "grant_type": "client_credentials",

       "audience": "https://topups-sandbox.reloadly.com"
      }
   </li>
   <li>
      <p>Click <strong>Send</strong>.</p>
   </li>
   <li>
      <p>View the sample response : </p>
    <code>
     {

      "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSU",

      "scope": "send-topups read-topups-history read-operators read-promotions",

      "expires_in": 86400,

      "token_type": "Bearer"
     }
   </li>
</ol>

Where : <br />
<table>
   <colgroup><col width="25%">
   <col width="75%">
   </colgroup><tbody><tr>
      <td>
         <code><var>access_token</var></code>
      </td>
      <td>Your access token.</td>
   </tr>
   <tr>
      <td><code>expires_in</code></td>
      <td>The number of seconds after which the token expires. Request another token when the current one expires.</td>
   </tr>
</tbody></table>

#### Make REST API Calls

<p>With a valid access token, you can make REST API calls.</p><br />
<p>This sample call sends a airtime (topup) transaction and uses only the required input parameters. The access token in the call is an OAuth bearer token.</p>
<br />
<blockquote class="dx-blockquote-note">
<p><strong>Note:</strong> Topups API calls are always made by an `actor`. The actor specifies a bearer token in the <code>Authorization: Bearer</code> request header. A bearer token is an access token that is issued to the actor by an authorization server with the approval of the resource owner. In this case, the actor uses the bearer token to make a topup request.</p>
</blockquote>

```
curl -d '{
          "recipientPhone": {
            "countryCode": "HT",
            "number": "36377111"
          },
          "senderPhone": {
            "countryCode": "US",
            "number": "3059547862"
          },
          "operatorId": 173,
          "amount": 15,
          "customIdentifier": "transaction by john@example.com"
        }' \
    -H "Accept: application/com.reloadly.topups-v1+json" \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSU" \
    -X POST https://topups.reloadly.com/topups
```

<br/><br /><br />

## API REFERENCE

<br />

## Topups API ###

-----------------

The Reloadly Topups API is RESTful and uses a JSON data format. The API grants users in more than 100 countries access to its feature set. The API enables users to conduct topup (airtime) transactions, retrieve account data, view international rates, see history and much more.
<br /><br />

#### Account Balance (resource group)

--------------------

Use the `/accounts/balance` resource to list account available balance.

## Actions

### accounts.balance.get
Retrieve account balance


```js
reloadly.accounts.balance.get(null, context)
```

#### Input
*This action has no parameters*

#### Output
*Output schema unknown*

### countries.get
List All Supported Countries


```js
reloadly.countries.get(null, context)
```

#### Input
*This action has no parameters*

#### Output
*Output schema unknown*

### countries.HT.get
See http://www.nationsonline.org/oneworld/country_code_list.htm
    - Endpoint : `/countries/{countryIsoCode}`


```js
reloadly.countries.HT.get(null, context)
```

#### Input
*This action has no parameters*

#### Output
*Output schema unknown*

### operators.get
List All Operators


```js
reloadly.operators.get(null, context)
```

#### Input
*This action has no parameters*

#### Output
*Output schema unknown*

### operators.173.get
- Endpoint : `/operators/{operatorId}`


```js
reloadly.operators.173.get(null, context)
```

#### Input
*This action has no parameters*

#### Output
*Output schema unknown*

### operators.173.commissions.get
- Endpoint : `/operators/{operatorId}/commissions`


```js
reloadly.operators.173.commissions.get(null, context)
```

#### Input
*This action has no parameters*

#### Output
*Output schema unknown*

### operators.auto_detect.phone.36377111.country_code.HT.get
- NOTE: Supports phone number without country dialing code or with country dialing code.
         Example : `+50936377111` or `36377111` are equivalent
                   `/operators/auto-detect/phone/{phone}/country-code/{countryIsoCode}?&includeBundles=true`


```js
reloadly.operators.auto_detect.phone.36377111.country_code.HT.get(null, context)
```

#### Input
*This action has no parameters*

#### Output
*Output schema unknown*

### operators.commissions.get
List All Commissions


```js
reloadly.operators.commissions.get(null, context)
```

#### Input
*This action has no parameters*

#### Output
*Output schema unknown*

### operators.countries.HT.get
- Endpoint : `/operators/countries/{countryIsoCode}`


```js
reloadly.operators.countries.HT.get(null, context)
```

#### Input
*This action has no parameters*

#### Output
*Output schema unknown*

### promotions.get
List all topup operators promotions


```js
reloadly.promotions.get(null, context)
```

#### Input
*This action has no parameters*

#### Output
*Output schema unknown*

### promotions.129.get
- Endpoint : `/promotions/{operatorId}`


```js
reloadly.promotions.129.get(null, context)
```

#### Input
*This action has no parameters*

#### Output
*Output schema unknown*

### promotions.5.get
- Endpoint : `/promotions/{promotionId}`


```js
reloadly.promotions.5.get(null, context)
```

#### Input
*This action has no parameters*

#### Output
*Output schema unknown*

### topups.post
- Endpoint : `/topups`


```js
reloadly.topups.post({}, context)
```

#### Input
* input `object`
  * body `object`
    * amount `number`
    * customIdentifier `string`
    * operatorId `number`
    * recipientPhone `object`
      * countryCode `string`
      * number `string`
    * senderPhone `object`
      * countryCode `string`
      * number `string`

#### Output
*Output schema unknown*

### topups.reports.transactions.get
- Endpoint : `/topups/reports/transactions?page=1&size=1&startTime=2018-06-01 00:00:00&endTime=2018-06-26 23:59:59`


```js
reloadly.topups.reports.transactions.get(null, context)
```

#### Input
*This action has no parameters*

#### Output
*Output schema unknown*



## Definitions

### Account_Balance


### Commissions_Collection


### Country_Collection


### Operators_Collection


### Promotions_Collection


### Topup_a_phone


### Transaction_History



