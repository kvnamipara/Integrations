# @datafire/amazonaws_waf_regional
This is the <i>AWS WAF Regional API Reference</i> for using AWS WAF with Elastic Load Balancing (ELB) Application Load Balancers. The AWS WAF actions and data types listed in the reference are available for protecting Application Load Balancers. You can use these actions and data types by means of the endpoints listed in <a href="http://docs.aws.amazon.com/general/latest/gr/rande.html#waf_region">AWS Regions and Endpoints</a>. This guide is for developers who need detailed information about the AWS WAF API actions, data types, and errors. For detailed information about AWS WAF features and an overview of how to use the AWS WAF API, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.

## Operation: AssociateWebACL
Associates a web ACL with a resource.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/AssociateWebACLRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/AssociateWebACLResponse"
}
```
## Operation: CreateByteMatchSet
<p>Creates a <code>ByteMatchSet</code>. You then use <a>UpdateByteMatchSet</a> to identify the part of a web request that you want AWS WAF to inspect, such as the values of the <code>User-Agent</code> header or the query string. For example, you can create a <code>ByteMatchSet</code> that matches any requests with <code>User-Agent</code> headers that contain the string <code>BadBot</code>. You can then configure AWS WAF to reject those requests.</p> <p>To create and configure a <code>ByteMatchSet</code>, perform the following steps:</p> <ol> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of a <code>CreateByteMatchSet</code> request.</p> </li> <li> <p>Submit a <code>CreateByteMatchSet</code> request.</p> </li> <li> <p>Use <code>GetChangeToken</code> to get the change token that you provide in the <code>ChangeToken</code> parameter of an <code>UpdateByteMatchSet</code> request.</p> </li> <li> <p>Submit an <a>UpdateByteMatchSet</a> request to specify the part of the request that you want AWS WAF to inspect (for example, the header or the URI) and the value that you want AWS WAF to watch for.</p> </li> </ol> <p>For more information about how to use the AWS WAF API to allow or block HTTP requests, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/CreateByteMatchSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/CreateByteMatchSetResponse"
}
```
## Operation: CreateIPSet
<p>Creates an <a>IPSet</a>, which you use to specify which web requests you want to allow or block based on the IP addresses that the requests originate from. For example, if you're receiving a lot of requests from one or more individual IP addresses or one or more ranges of IP addresses and you want to block the requests, you can create an <code>IPSet</code> that contains those IP addresses and then configure AWS WAF to block the requests. </p> <p>To create and configure an <code>IPSet</code>, perform the following steps:</p> <ol> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of a <code>CreateIPSet</code> request.</p> </li> <li> <p>Submit a <code>CreateIPSet</code> request.</p> </li> <li> <p>Use <code>GetChangeToken</code> to get the change token that you provide in the <code>ChangeToken</code> parameter of an <a>UpdateIPSet</a> request.</p> </li> <li> <p>Submit an <code>UpdateIPSet</code> request to specify the IP addresses that you want AWS WAF to watch for.</p> </li> </ol> <p>For more information about how to use the AWS WAF API to allow or block HTTP requests, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/CreateIPSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/CreateIPSetResponse"
}
```
## Operation: CreateRule
<p>Creates a <code>Rule</code>, which contains the <code>IPSet</code> objects, <code>ByteMatchSet</code> objects, and other predicates that identify the requests that you want to block. If you add more than one predicate to a <code>Rule</code>, a request must match all of the specifications to be allowed or blocked. For example, suppose you add the following to a <code>Rule</code>:</p> <ul> <li> <p>An <code>IPSet</code> that matches the IP address <code>192.0.2.44/32</code> </p> </li> <li> <p>A <code>ByteMatchSet</code> that matches <code>BadBot</code> in the <code>User-Agent</code> header</p> </li> </ul> <p>You then add the <code>Rule</code> to a <code>WebACL</code> and specify that you want to blocks requests that satisfy the <code>Rule</code>. For a request to be blocked, it must come from the IP address 192.0.2.44 <i>and</i> the <code>User-Agent</code> header in the request must contain the value <code>BadBot</code>.</p> <p>To create and configure a <code>Rule</code>, perform the following steps:</p> <ol> <li> <p>Create and update the predicates that you want to include in the <code>Rule</code>. For more information, see <a>CreateByteMatchSet</a>, <a>CreateIPSet</a>, and <a>CreateSqlInjectionMatchSet</a>.</p> </li> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of a <code>CreateRule</code> request.</p> </li> <li> <p>Submit a <code>CreateRule</code> request.</p> </li> <li> <p>Use <code>GetChangeToken</code> to get the change token that you provide in the <code>ChangeToken</code> parameter of an <a>UpdateRule</a> request.</p> </li> <li> <p>Submit an <code>UpdateRule</code> request to specify the predicates that you want to include in the <code>Rule</code>.</p> </li> <li> <p>Create and update a <code>WebACL</code> that contains the <code>Rule</code>. For more information, see <a>CreateWebACL</a>.</p> </li> </ol> <p>For more information about how to use the AWS WAF API to allow or block HTTP requests, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/CreateRuleRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/CreateRuleResponse"
}
```
## Operation: CreateSizeConstraintSet
<p>Creates a <code>SizeConstraintSet</code>. You then use <a>UpdateSizeConstraintSet</a> to identify the part of a web request that you want AWS WAF to check for length, such as the length of the <code>User-Agent</code> header or the length of the query string. For example, you can create a <code>SizeConstraintSet</code> that matches any requests that have a query string that is longer than 100 bytes. You can then configure AWS WAF to reject those requests.</p> <p>To create and configure a <code>SizeConstraintSet</code>, perform the following steps:</p> <ol> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of a <code>CreateSizeConstraintSet</code> request.</p> </li> <li> <p>Submit a <code>CreateSizeConstraintSet</code> request.</p> </li> <li> <p>Use <code>GetChangeToken</code> to get the change token that you provide in the <code>ChangeToken</code> parameter of an <code>UpdateSizeConstraintSet</code> request.</p> </li> <li> <p>Submit an <a>UpdateSizeConstraintSet</a> request to specify the part of the request that you want AWS WAF to inspect (for example, the header or the URI) and the value that you want AWS WAF to watch for.</p> </li> </ol> <p>For more information about how to use the AWS WAF API to allow or block HTTP requests, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/CreateSizeConstraintSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/CreateSizeConstraintSetResponse"
}
```
## Operation: CreateSqlInjectionMatchSet
<p>Creates a <a>SqlInjectionMatchSet</a>, which you use to allow, block, or count requests that contain snippets of SQL code in a specified part of web requests. AWS WAF searches for character sequences that are likely to be malicious strings.</p> <p>To create and configure a <code>SqlInjectionMatchSet</code>, perform the following steps:</p> <ol> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of a <code>CreateSqlInjectionMatchSet</code> request.</p> </li> <li> <p>Submit a <code>CreateSqlInjectionMatchSet</code> request.</p> </li> <li> <p>Use <code>GetChangeToken</code> to get the change token that you provide in the <code>ChangeToken</code> parameter of an <a>UpdateSqlInjectionMatchSet</a> request.</p> </li> <li> <p>Submit an <a>UpdateSqlInjectionMatchSet</a> request to specify the parts of web requests in which you want to allow, block, or count malicious SQL code.</p> </li> </ol> <p>For more information about how to use the AWS WAF API to allow or block HTTP requests, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/CreateSqlInjectionMatchSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/CreateSqlInjectionMatchSetResponse"
}
```
## Operation: CreateWebACL
<p>Creates a <code>WebACL</code>, which contains the <code>Rules</code> that identify the CloudFront web requests that you want to allow, block, or count. AWS WAF evaluates <code>Rules</code> in order based on the value of <code>Priority</code> for each <code>Rule</code>.</p> <p>You also specify a default action, either <code>ALLOW</code> or <code>BLOCK</code>. If a web request doesn't match any of the <code>Rules</code> in a <code>WebACL</code>, AWS WAF responds to the request with the default action. </p> <p>To create and configure a <code>WebACL</code>, perform the following steps:</p> <ol> <li> <p>Create and update the <code>ByteMatchSet</code> objects and other predicates that you want to include in <code>Rules</code>. For more information, see <a>CreateByteMatchSet</a>, <a>UpdateByteMatchSet</a>, <a>CreateIPSet</a>, <a>UpdateIPSet</a>, <a>CreateSqlInjectionMatchSet</a>, and <a>UpdateSqlInjectionMatchSet</a>.</p> </li> <li> <p>Create and update the <code>Rules</code> that you want to include in the <code>WebACL</code>. For more information, see <a>CreateRule</a> and <a>UpdateRule</a>.</p> </li> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of a <code>CreateWebACL</code> request.</p> </li> <li> <p>Submit a <code>CreateWebACL</code> request.</p> </li> <li> <p>Use <code>GetChangeToken</code> to get the change token that you provide in the <code>ChangeToken</code> parameter of an <a>UpdateWebACL</a> request.</p> </li> <li> <p>Submit an <a>UpdateWebACL</a> request to specify the <code>Rules</code> that you want to include in the <code>WebACL</code>, to specify the default action, and to associate the <code>WebACL</code> with a CloudFront distribution.</p> </li> </ol> <p>For more information about how to use the AWS WAF API, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/CreateWebACLRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/CreateWebACLResponse"
}
```
## Operation: CreateXssMatchSet
<p>Creates an <a>XssMatchSet</a>, which you use to allow, block, or count requests that contain cross-site scripting attacks in the specified part of web requests. AWS WAF searches for character sequences that are likely to be malicious strings.</p> <p>To create and configure an <code>XssMatchSet</code>, perform the following steps:</p> <ol> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of a <code>CreateXssMatchSet</code> request.</p> </li> <li> <p>Submit a <code>CreateXssMatchSet</code> request.</p> </li> <li> <p>Use <code>GetChangeToken</code> to get the change token that you provide in the <code>ChangeToken</code> parameter of an <a>UpdateXssMatchSet</a> request.</p> </li> <li> <p>Submit an <a>UpdateXssMatchSet</a> request to specify the parts of web requests in which you want to allow, block, or count cross-site scripting attacks.</p> </li> </ol> <p>For more information about how to use the AWS WAF API to allow or block HTTP requests, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/CreateXssMatchSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/CreateXssMatchSetResponse"
}
```
## Operation: DeleteByteMatchSet
<p>Permanently deletes a <a>ByteMatchSet</a>. You can't delete a <code>ByteMatchSet</code> if it's still used in any <code>Rules</code> or if it still includes any <a>ByteMatchTuple</a> objects (any filters).</p> <p>If you just want to remove a <code>ByteMatchSet</code> from a <code>Rule</code>, use <a>UpdateRule</a>.</p> <p>To permanently delete a <code>ByteMatchSet</code>, perform the following steps:</p> <ol> <li> <p>Update the <code>ByteMatchSet</code> to remove filters, if any. For more information, see <a>UpdateByteMatchSet</a>.</p> </li> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of a <code>DeleteByteMatchSet</code> request.</p> </li> <li> <p>Submit a <code>DeleteByteMatchSet</code> request.</p> </li> </ol>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/DeleteByteMatchSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/DeleteByteMatchSetResponse"
}
```
## Operation: DeleteIPSet
<p>Permanently deletes an <a>IPSet</a>. You can't delete an <code>IPSet</code> if it's still used in any <code>Rules</code> or if it still includes any IP addresses.</p> <p>If you just want to remove an <code>IPSet</code> from a <code>Rule</code>, use <a>UpdateRule</a>.</p> <p>To permanently delete an <code>IPSet</code> from AWS WAF, perform the following steps:</p> <ol> <li> <p>Update the <code>IPSet</code> to remove IP address ranges, if any. For more information, see <a>UpdateIPSet</a>.</p> </li> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of a <code>DeleteIPSet</code> request.</p> </li> <li> <p>Submit a <code>DeleteIPSet</code> request.</p> </li> </ol>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/DeleteIPSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/DeleteIPSetResponse"
}
```
## Operation: DeleteRule
<p>Permanently deletes a <a>Rule</a>. You can't delete a <code>Rule</code> if it's still used in any <code>WebACL</code> objects or if it still includes any predicates, such as <code>ByteMatchSet</code> objects.</p> <p>If you just want to remove a <code>Rule</code> from a <code>WebACL</code>, use <a>UpdateWebACL</a>.</p> <p>To permanently delete a <code>Rule</code> from AWS WAF, perform the following steps:</p> <ol> <li> <p>Update the <code>Rule</code> to remove predicates, if any. For more information, see <a>UpdateRule</a>.</p> </li> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of a <code>DeleteRule</code> request.</p> </li> <li> <p>Submit a <code>DeleteRule</code> request.</p> </li> </ol>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/DeleteRuleRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/DeleteRuleResponse"
}
```
## Operation: DeleteSizeConstraintSet
<p>Permanently deletes a <a>SizeConstraintSet</a>. You can't delete a <code>SizeConstraintSet</code> if it's still used in any <code>Rules</code> or if it still includes any <a>SizeConstraint</a> objects (any filters).</p> <p>If you just want to remove a <code>SizeConstraintSet</code> from a <code>Rule</code>, use <a>UpdateRule</a>.</p> <p>To permanently delete a <code>SizeConstraintSet</code>, perform the following steps:</p> <ol> <li> <p>Update the <code>SizeConstraintSet</code> to remove filters, if any. For more information, see <a>UpdateSizeConstraintSet</a>.</p> </li> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of a <code>DeleteSizeConstraintSet</code> request.</p> </li> <li> <p>Submit a <code>DeleteSizeConstraintSet</code> request.</p> </li> </ol>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/DeleteSizeConstraintSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/DeleteSizeConstraintSetResponse"
}
```
## Operation: DeleteSqlInjectionMatchSet
<p>Permanently deletes a <a>SqlInjectionMatchSet</a>. You can't delete a <code>SqlInjectionMatchSet</code> if it's still used in any <code>Rules</code> or if it still contains any <a>SqlInjectionMatchTuple</a> objects.</p> <p>If you just want to remove a <code>SqlInjectionMatchSet</code> from a <code>Rule</code>, use <a>UpdateRule</a>.</p> <p>To permanently delete a <code>SqlInjectionMatchSet</code> from AWS WAF, perform the following steps:</p> <ol> <li> <p>Update the <code>SqlInjectionMatchSet</code> to remove filters, if any. For more information, see <a>UpdateSqlInjectionMatchSet</a>.</p> </li> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of a <code>DeleteSqlInjectionMatchSet</code> request.</p> </li> <li> <p>Submit a <code>DeleteSqlInjectionMatchSet</code> request.</p> </li> </ol>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/DeleteSqlInjectionMatchSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/DeleteSqlInjectionMatchSetResponse"
}
```
## Operation: DeleteWebACL
<p>Permanently deletes a <a>WebACL</a>. You can't delete a <code>WebACL</code> if it still contains any <code>Rules</code>.</p> <p>To delete a <code>WebACL</code>, perform the following steps:</p> <ol> <li> <p>Update the <code>WebACL</code> to remove <code>Rules</code>, if any. For more information, see <a>UpdateWebACL</a>.</p> </li> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of a <code>DeleteWebACL</code> request.</p> </li> <li> <p>Submit a <code>DeleteWebACL</code> request.</p> </li> </ol>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/DeleteWebACLRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/DeleteWebACLResponse"
}
```
## Operation: DeleteXssMatchSet
<p>Permanently deletes an <a>XssMatchSet</a>. You can't delete an <code>XssMatchSet</code> if it's still used in any <code>Rules</code> or if it still contains any <a>XssMatchTuple</a> objects.</p> <p>If you just want to remove an <code>XssMatchSet</code> from a <code>Rule</code>, use <a>UpdateRule</a>.</p> <p>To permanently delete an <code>XssMatchSet</code> from AWS WAF, perform the following steps:</p> <ol> <li> <p>Update the <code>XssMatchSet</code> to remove filters, if any. For more information, see <a>UpdateXssMatchSet</a>.</p> </li> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of a <code>DeleteXssMatchSet</code> request.</p> </li> <li> <p>Submit a <code>DeleteXssMatchSet</code> request.</p> </li> </ol>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/DeleteXssMatchSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/DeleteXssMatchSetResponse"
}
```
## Operation: DisassociateWebACL
Removes a web ACL from the specified resource.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/DisassociateWebACLRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/DisassociateWebACLResponse"
}
```
## Operation: GetByteMatchSet
Returns the <a>ByteMatchSet</a> specified by <code>ByteMatchSetId</code>.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/GetByteMatchSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/GetByteMatchSetResponse"
}
```
## Operation: GetChangeToken
<p>When you want to create, update, or delete AWS WAF objects, get a change token and include the change token in the create, update, or delete request. Change tokens ensure that your application doesn't submit conflicting requests to AWS WAF.</p> <p>Each create, update, or delete request must use a unique change token. If your application submits a <code>GetChangeToken</code> request and then submits a second <code>GetChangeToken</code> request before submitting a create, update, or delete request, the second <code>GetChangeToken</code> request returns the same value as the first <code>GetChangeToken</code> request.</p> <p>When you use a change token in a create, update, or delete request, the status of the change token changes to <code>PENDING</code>, which indicates that AWS WAF is propagating the change to all AWS WAF servers. Use <code>GetChangeTokenStatus</code> to determine the status of your change token.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/GetChangeTokenRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/GetChangeTokenResponse"
}
```
## Operation: GetChangeTokenStatus
<p>Returns the status of a <code>ChangeToken</code> that you got by calling <a>GetChangeToken</a>. <code>ChangeTokenStatus</code> is one of the following values:</p> <ul> <li> <p> <code>PROVISIONED</code>: You requested the change token by calling <code>GetChangeToken</code>, but you haven't used it yet in a call to create, update, or delete an AWS WAF object.</p> </li> <li> <p> <code>PENDING</code>: AWS WAF is propagating the create, update, or delete request to all AWS WAF servers.</p> </li> <li> <p> <code>IN_SYNC</code>: Propagation is complete.</p> </li> </ul>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/GetChangeTokenStatusRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/GetChangeTokenStatusResponse"
}
```
## Operation: GetIPSet
Returns the <a>IPSet</a> that is specified by <code>IPSetId</code>.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/GetIPSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/GetIPSetResponse"
}
```
## Operation: GetRule
Returns the <a>Rule</a> that is specified by the <code>RuleId</code> that you included in the <code>GetRule</code> request.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/GetRuleRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/GetRuleResponse"
}
```
## Operation: GetSampledRequests
<p>Gets detailed information about a specified number of requests--a sample--that AWS WAF randomly selects from among the first 5,000 requests that your AWS resource received during a time range that you choose. You can specify a sample size of up to 500 requests, and you can specify any time range in the previous three hours.</p> <p> <code>GetSampledRequests</code> returns a time range, which is usually the time range that you specified. However, if your resource (such as a CloudFront distribution) received 5,000 requests before the specified time range elapsed, <code>GetSampledRequests</code> returns an updated time range. This new time range indicates the actual period during which AWS WAF selected the requests in the sample.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/GetSampledRequestsRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/GetSampledRequestsResponse"
}
```
## Operation: GetSizeConstraintSet
Returns the <a>SizeConstraintSet</a> specified by <code>SizeConstraintSetId</code>.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/GetSizeConstraintSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/GetSizeConstraintSetResponse"
}
```
## Operation: GetSqlInjectionMatchSet
Returns the <a>SqlInjectionMatchSet</a> that is specified by <code>SqlInjectionMatchSetId</code>.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/GetSqlInjectionMatchSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/GetSqlInjectionMatchSetResponse"
}
```
## Operation: GetWebACL
Returns the <a>WebACL</a> that is specified by <code>WebACLId</code>.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/GetWebACLRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/GetWebACLResponse"
}
```
## Operation: GetWebACLForResource
Returns the web ACL for the specified resource.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/GetWebACLForResourceRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/GetWebACLForResourceResponse"
}
```
## Operation: GetXssMatchSet
Returns the <a>XssMatchSet</a> that is specified by <code>XssMatchSetId</code>.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/GetXssMatchSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/GetXssMatchSetResponse"
}
```
## Operation: ListByteMatchSets
Returns an array of <a>ByteMatchSetSummary</a> objects.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/ListByteMatchSetsRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ListByteMatchSetsResponse"
}
```
## Operation: ListIPSets
Returns an array of <a>IPSetSummary</a> objects in the response.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/ListIPSetsRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ListIPSetsResponse"
}
```
## Operation: ListResourcesForWebACL
Returns an array of resources associated with the specified web ACL.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/ListResourcesForWebACLRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ListResourcesForWebACLResponse"
}
```
## Operation: ListRules
Returns an array of <a>RuleSummary</a> objects.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/ListRulesRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ListRulesResponse"
}
```
## Operation: ListSizeConstraintSets
Returns an array of <a>SizeConstraintSetSummary</a> objects.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/ListSizeConstraintSetsRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ListSizeConstraintSetsResponse"
}
```
## Operation: ListSqlInjectionMatchSets
Returns an array of <a>SqlInjectionMatchSet</a> objects.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/ListSqlInjectionMatchSetsRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ListSqlInjectionMatchSetsResponse"
}
```
## Operation: ListWebACLs
Returns an array of <a>WebACLSummary</a> objects in the response.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/ListWebACLsRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ListWebACLsResponse"
}
```
## Operation: ListXssMatchSets
Returns an array of <a>XssMatchSet</a> objects.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/ListXssMatchSetsRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ListXssMatchSetsResponse"
}
```
## Operation: UpdateByteMatchSet
<p>Inserts or deletes <a>ByteMatchTuple</a> objects (filters) in a <a>ByteMatchSet</a>. For each <code>ByteMatchTuple</code> object, you specify the following values: </p> <ul> <li> <p>Whether to insert or delete the object from the array. If you want to change a <code>ByteMatchSetUpdate</code> object, you delete the existing object and add a new one.</p> </li> <li> <p>The part of a web request that you want AWS WAF to inspect, such as a query string or the value of the <code>User-Agent</code> header. </p> </li> <li> <p>The bytes (typically a string that corresponds with ASCII characters) that you want AWS WAF to look for. For more information, including how you specify the values for the AWS WAF API and the AWS CLI or SDKs, see <code>TargetString</code> in the <a>ByteMatchTuple</a> data type. </p> </li> <li> <p>Where to look, such as at the beginning or the end of a query string.</p> </li> <li> <p>Whether to perform any conversions on the request, such as converting it to lowercase, before inspecting it for the specified string.</p> </li> </ul> <p>For example, you can add a <code>ByteMatchSetUpdate</code> object that matches web requests in which <code>User-Agent</code> headers contain the string <code>BadBot</code>. You can then configure AWS WAF to block those requests.</p> <p>To create and configure a <code>ByteMatchSet</code>, perform the following steps:</p> <ol> <li> <p>Create a <code>ByteMatchSet.</code> For more information, see <a>CreateByteMatchSet</a>.</p> </li> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of an <code>UpdateByteMatchSet</code> request.</p> </li> <li> <p>Submit an <code>UpdateByteMatchSet</code> request to specify the part of the request that you want AWS WAF to inspect (for example, the header or the URI) and the value that you want AWS WAF to watch for.</p> </li> </ol> <p>For more information about how to use the AWS WAF API to allow or block HTTP requests, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/UpdateByteMatchSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/UpdateByteMatchSetResponse"
}
```
## Operation: UpdateIPSet
<p>Inserts or deletes <a>IPSetDescriptor</a> objects in an <code>IPSet</code>. For each <code>IPSetDescriptor</code> object, you specify the following values: </p> <ul> <li> <p>Whether to insert or delete the object from the array. If you want to change an <code>IPSetDescriptor</code> object, you delete the existing object and add a new one.</p> </li> <li> <p>The IP address version, <code>IPv4</code> or <code>IPv6</code>. </p> </li> <li> <p>The IP address in CIDR notation, for example, <code>192.0.2.0/24</code> (for the range of IP addresses from <code>192.0.2.0</code> to <code>192.0.2.255</code>) or <code>192.0.2.44/32</code> (for the individual IP address <code>192.0.2.44</code>). </p> </li> </ul> <p>AWS WAF supports /8, /16, /24, and /32 IP address ranges for IPv4, and /24, /32, /48, /56, /64 and /128 for IPv6. For more information about CIDR notation, see the Wikipedia entry <a href="https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing">Classless Inter-Domain Routing</a>.</p> <p>IPv6 addresses can be represented using any of the following formats:</p> <ul> <li> <p>1111:0000:0000:0000:0000:0000:0000:0111/128</p> </li> <li> <p>1111:0:0:0:0:0:0:0111/128</p> </li> <li> <p>1111::0111/128</p> </li> <li> <p>1111::111/128</p> </li> </ul> <p>You use an <code>IPSet</code> to specify which web requests you want to allow or block based on the IP addresses that the requests originated from. For example, if you're receiving a lot of requests from one or a small number of IP addresses and you want to block the requests, you can create an <code>IPSet</code> that specifies those IP addresses, and then configure AWS WAF to block the requests. </p> <p>To create and configure an <code>IPSet</code>, perform the following steps:</p> <ol> <li> <p>Submit a <a>CreateIPSet</a> request.</p> </li> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of an <a>UpdateIPSet</a> request.</p> </li> <li> <p>Submit an <code>UpdateIPSet</code> request to specify the IP addresses that you want AWS WAF to watch for.</p> </li> </ol> <p>When you update an <code>IPSet</code>, you specify the IP addresses that you want to add and/or the IP addresses that you want to delete. If you want to change an IP address, you delete the existing IP address and add the new one.</p> <p>For more information about how to use the AWS WAF API to allow or block HTTP requests, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/UpdateIPSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/UpdateIPSetResponse"
}
```
## Operation: UpdateRule
<p>Inserts or deletes <a>Predicate</a> objects in a <code>Rule</code>. Each <code>Predicate</code> object identifies a predicate, such as a <a>ByteMatchSet</a> or an <a>IPSet</a>, that specifies the web requests that you want to allow, block, or count. If you add more than one predicate to a <code>Rule</code>, a request must match all of the specifications to be allowed, blocked, or counted. For example, suppose you add the following to a <code>Rule</code>: </p> <ul> <li> <p>A <code>ByteMatchSet</code> that matches the value <code>BadBot</code> in the <code>User-Agent</code> header</p> </li> <li> <p>An <code>IPSet</code> that matches the IP address <code>192.0.2.44</code> </p> </li> </ul> <p>You then add the <code>Rule</code> to a <code>WebACL</code> and specify that you want to block requests that satisfy the <code>Rule</code>. For a request to be blocked, the <code>User-Agent</code> header in the request must contain the value <code>BadBot</code> <i>and</i> the request must originate from the IP address 192.0.2.44.</p> <p>To create and configure a <code>Rule</code>, perform the following steps:</p> <ol> <li> <p>Create and update the predicates that you want to include in the <code>Rule</code>.</p> </li> <li> <p>Create the <code>Rule</code>. See <a>CreateRule</a>.</p> </li> <li> <p>Use <code>GetChangeToken</code> to get the change token that you provide in the <code>ChangeToken</code> parameter of an <a>UpdateRule</a> request.</p> </li> <li> <p>Submit an <code>UpdateRule</code> request to add predicates to the <code>Rule</code>.</p> </li> <li> <p>Create and update a <code>WebACL</code> that contains the <code>Rule</code>. See <a>CreateWebACL</a>.</p> </li> </ol> <p>If you want to replace one <code>ByteMatchSet</code> or <code>IPSet</code> with another, you delete the existing one and add the new one.</p> <p>For more information about how to use the AWS WAF API to allow or block HTTP requests, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/UpdateRuleRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/UpdateRuleResponse"
}
```
## Operation: UpdateSizeConstraintSet
<p>Inserts or deletes <a>SizeConstraint</a> objects (filters) in a <a>SizeConstraintSet</a>. For each <code>SizeConstraint</code> object, you specify the following values: </p> <ul> <li> <p>Whether to insert or delete the object from the array. If you want to change a <code>SizeConstraintSetUpdate</code> object, you delete the existing object and add a new one.</p> </li> <li> <p>The part of a web request that you want AWS WAF to evaluate, such as the length of a query string or the length of the <code>User-Agent</code> header.</p> </li> <li> <p>Whether to perform any transformations on the request, such as converting it to lowercase, before checking its length. Note that transformations of the request body are not supported because the AWS resource forwards only the first <code>8192</code> bytes of your request to AWS WAF.</p> </li> <li> <p>A <code>ComparisonOperator</code> used for evaluating the selected part of the request against the specified <code>Size</code>, such as equals, greater than, less than, and so on.</p> </li> <li> <p>The length, in bytes, that you want AWS WAF to watch for in selected part of the request. The length is computed after applying the transformation.</p> </li> </ul> <p>For example, you can add a <code>SizeConstraintSetUpdate</code> object that matches web requests in which the length of the <code>User-Agent</code> header is greater than 100 bytes. You can then configure AWS WAF to block those requests.</p> <p>To create and configure a <code>SizeConstraintSet</code>, perform the following steps:</p> <ol> <li> <p>Create a <code>SizeConstraintSet.</code> For more information, see <a>CreateSizeConstraintSet</a>.</p> </li> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of an <code>UpdateSizeConstraintSet</code> request.</p> </li> <li> <p>Submit an <code>UpdateSizeConstraintSet</code> request to specify the part of the request that you want AWS WAF to inspect (for example, the header or the URI) and the value that you want AWS WAF to watch for.</p> </li> </ol> <p>For more information about how to use the AWS WAF API to allow or block HTTP requests, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/UpdateSizeConstraintSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/UpdateSizeConstraintSetResponse"
}
```
## Operation: UpdateSqlInjectionMatchSet
<p>Inserts or deletes <a>SqlInjectionMatchTuple</a> objects (filters) in a <a>SqlInjectionMatchSet</a>. For each <code>SqlInjectionMatchTuple</code> object, you specify the following values:</p> <ul> <li> <p> <code>Action</code>: Whether to insert the object into or delete the object from the array. To change a <code>SqlInjectionMatchTuple</code>, you delete the existing object and add a new one.</p> </li> <li> <p> <code>FieldToMatch</code>: The part of web requests that you want AWS WAF to inspect and, if you want AWS WAF to inspect a header, the name of the header.</p> </li> <li> <p> <code>TextTransformation</code>: Which text transformation, if any, to perform on the web request before inspecting the request for snippets of malicious SQL code.</p> </li> </ul> <p>You use <code>SqlInjectionMatchSet</code> objects to specify which CloudFront requests you want to allow, block, or count. For example, if you're receiving requests that contain snippets of SQL code in the query string and you want to block the requests, you can create a <code>SqlInjectionMatchSet</code> with the applicable settings, and then configure AWS WAF to block the requests. </p> <p>To create and configure a <code>SqlInjectionMatchSet</code>, perform the following steps:</p> <ol> <li> <p>Submit a <a>CreateSqlInjectionMatchSet</a> request.</p> </li> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of an <a>UpdateIPSet</a> request.</p> </li> <li> <p>Submit an <code>UpdateSqlInjectionMatchSet</code> request to specify the parts of web requests that you want AWS WAF to inspect for snippets of SQL code.</p> </li> </ol> <p>For more information about how to use the AWS WAF API to allow or block HTTP requests, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/UpdateSqlInjectionMatchSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/UpdateSqlInjectionMatchSetResponse"
}
```
## Operation: UpdateWebACL
<p>Inserts or deletes <a>ActivatedRule</a> objects in a <code>WebACL</code>. Each <code>Rule</code> identifies web requests that you want to allow, block, or count. When you update a <code>WebACL</code>, you specify the following values:</p> <ul> <li> <p>A default action for the <code>WebACL</code>, either <code>ALLOW</code> or <code>BLOCK</code>. AWS WAF performs the default action if a request doesn't match the criteria in any of the <code>Rules</code> in a <code>WebACL</code>.</p> </li> <li> <p>The <code>Rules</code> that you want to add and/or delete. If you want to replace one <code>Rule</code> with another, you delete the existing <code>Rule</code> and add the new one.</p> </li> <li> <p>For each <code>Rule</code>, whether you want AWS WAF to allow requests, block requests, or count requests that match the conditions in the <code>Rule</code>.</p> </li> <li> <p>The order in which you want AWS WAF to evaluate the <code>Rules</code> in a <code>WebACL</code>. If you add more than one <code>Rule</code> to a <code>WebACL</code>, AWS WAF evaluates each request against the <code>Rules</code> in order based on the value of <code>Priority</code>. (The <code>Rule</code> that has the lowest value for <code>Priority</code> is evaluated first.) When a web request matches all of the predicates (such as <code>ByteMatchSets</code> and <code>IPSets</code>) in a <code>Rule</code>, AWS WAF immediately takes the corresponding action, allow or block, and doesn't evaluate the request against the remaining <code>Rules</code> in the <code>WebACL</code>, if any. </p> </li> </ul> <p>To create and configure a <code>WebACL</code>, perform the following steps:</p> <ol> <li> <p>Create and update the predicates that you want to include in <code>Rules</code>. For more information, see <a>CreateByteMatchSet</a>, <a>UpdateByteMatchSet</a>, <a>CreateIPSet</a>, <a>UpdateIPSet</a>, <a>CreateSqlInjectionMatchSet</a>, and <a>UpdateSqlInjectionMatchSet</a>.</p> </li> <li> <p>Create and update the <code>Rules</code> that you want to include in the <code>WebACL</code>. For more information, see <a>CreateRule</a> and <a>UpdateRule</a>.</p> </li> <li> <p>Create a <code>WebACL</code>. See <a>CreateWebACL</a>.</p> </li> <li> <p>Use <code>GetChangeToken</code> to get the change token that you provide in the <code>ChangeToken</code> parameter of an <a>UpdateWebACL</a> request.</p> </li> <li> <p>Submit an <code>UpdateWebACL</code> request to specify the <code>Rules</code> that you want to include in the <code>WebACL</code>, to specify the default action, and to associate the <code>WebACL</code> with a CloudFront distribution. </p> </li> </ol> <p>For more information about how to use the AWS WAF API to allow or block HTTP requests, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/UpdateWebACLRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/UpdateWebACLResponse"
}
```
## Operation: UpdateXssMatchSet
<p>Inserts or deletes <a>XssMatchTuple</a> objects (filters) in an <a>XssMatchSet</a>. For each <code>XssMatchTuple</code> object, you specify the following values:</p> <ul> <li> <p> <code>Action</code>: Whether to insert the object into or delete the object from the array. To change a <code>XssMatchTuple</code>, you delete the existing object and add a new one.</p> </li> <li> <p> <code>FieldToMatch</code>: The part of web requests that you want AWS WAF to inspect and, if you want AWS WAF to inspect a header, the name of the header.</p> </li> <li> <p> <code>TextTransformation</code>: Which text transformation, if any, to perform on the web request before inspecting the request for cross-site scripting attacks.</p> </li> </ul> <p>You use <code>XssMatchSet</code> objects to specify which CloudFront requests you want to allow, block, or count. For example, if you're receiving requests that contain cross-site scripting attacks in the request body and you want to block the requests, you can create an <code>XssMatchSet</code> with the applicable settings, and then configure AWS WAF to block the requests. </p> <p>To create and configure an <code>XssMatchSet</code>, perform the following steps:</p> <ol> <li> <p>Submit a <a>CreateXssMatchSet</a> request.</p> </li> <li> <p>Use <a>GetChangeToken</a> to get the change token that you provide in the <code>ChangeToken</code> parameter of an <a>UpdateIPSet</a> request.</p> </li> <li> <p>Submit an <code>UpdateXssMatchSet</code> request to specify the parts of web requests that you want AWS WAF to inspect for cross-site scripting attacks.</p> </li> </ol> <p>For more information about how to use the AWS WAF API to allow or block HTTP requests, see the <a href="http://docs.aws.amazon.com/waf/latest/developerguide/">AWS WAF Developer Guide</a>.</p>

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "body": {
      "$ref": "#/definitions/UpdateXssMatchSetRequest"
    },
    "Action": {
      "type": "string"
    },
    "Version": {
      "type": "string"
    },
    "X-Amz-Content-Sha256": {
      "type": "string"
    },
    "X-Amz-Date": {
      "type": "string"
    },
    "X-Amz-Algorithm": {
      "type": "string"
    },
    "X-Amz-Credential": {
      "type": "string"
    },
    "X-Amz-Security-Token": {
      "type": "string"
    },
    "X-Amz-Signature": {
      "type": "string"
    },
    "X-Amz-SignedHeaders": {
      "type": "string"
    }
  },
  "additionalProperties": false,
  "required": [
    "body",
    "Action",
    "Version"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/UpdateXssMatchSetResponse"
}
```