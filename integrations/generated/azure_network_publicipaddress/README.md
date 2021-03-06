# @datafire/azure_network_publicipaddress

Client library for NetworkManagementClient

## Installation and Usage
```bash
npm install --save @datafire/azure_network_publicipaddress
```
```js
let azure_network_publicipaddress = require('@datafire/azure_network_publicipaddress').create({
  access_token: "",
  refresh_token: "",
  client_id: "",
  client_secret: "",
  redirect_uri: ""
});

azure_network_publicipaddress.PublicIPAddresses_ListAll({
  "api-version": "",
  "subscriptionId": ""
}).then(data => {
  console.log(data);
});
```

## Description

The Microsoft Azure Network management API provides a RESTful set of web services that interact with Microsoft Azure Networks service to manage your network resources. The API has entities that capture the relationship between an end user and the Microsoft Azure Networks service.

## Actions

### PublicIPAddresses_ListAll
Gets all the public IP addresses in a subscription.


```js
azure_network_publicipaddress.PublicIPAddresses_ListAll({
  "api-version": "",
  "subscriptionId": ""
}, context)
```

#### Input
* input `object`
  * api-version **required** `string`: Client API version.
  * subscriptionId **required** `string`: The subscription credentials which uniquely identify the Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.

#### Output
* output [PublicIPAddressListResult](#publicipaddresslistresult)

### PublicIPAddresses_List
Gets all public IP addresses in a resource group.


```js
azure_network_publicipaddress.PublicIPAddresses_List({
  "resourceGroupName": "",
  "api-version": "",
  "subscriptionId": ""
}, context)
```

#### Input
* input `object`
  * resourceGroupName **required** `string`: The name of the resource group.
  * api-version **required** `string`: Client API version.
  * subscriptionId **required** `string`: The subscription credentials which uniquely identify the Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.

#### Output
* output [PublicIPAddressListResult](#publicipaddresslistresult)

### PublicIPAddresses_Delete
Deletes the specified public IP address.


```js
azure_network_publicipaddress.PublicIPAddresses_Delete({
  "resourceGroupName": "",
  "publicIpAddressName": "",
  "api-version": "",
  "subscriptionId": ""
}, context)
```

#### Input
* input `object`
  * resourceGroupName **required** `string`: The name of the resource group.
  * publicIpAddressName **required** `string`: The name of the subnet.
  * api-version **required** `string`: Client API version.
  * subscriptionId **required** `string`: The subscription credentials which uniquely identify the Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.

#### Output
*Output schema unknown*

### PublicIPAddresses_Get
Gets the specified public IP address in a specified resource group.


```js
azure_network_publicipaddress.PublicIPAddresses_Get({
  "resourceGroupName": "",
  "publicIpAddressName": "",
  "api-version": "",
  "subscriptionId": ""
}, context)
```

#### Input
* input `object`
  * resourceGroupName **required** `string`: The name of the resource group.
  * publicIpAddressName **required** `string`: The name of the subnet.
  * api-version **required** `string`: Client API version.
  * subscriptionId **required** `string`: The subscription credentials which uniquely identify the Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.
  * $expand `string`: Expands referenced resources.

#### Output
* output [PublicIPAddress](#publicipaddress)

### PublicIPAddresses_UpdateTags
Updates public IP address tags.


```js
azure_network_publicipaddress.PublicIPAddresses_UpdateTags({
  "resourceGroupName": "",
  "publicIpAddressName": "",
  "parameters": null,
  "api-version": "",
  "subscriptionId": ""
}, context)
```

#### Input
* input `object`
  * resourceGroupName **required** `string`: The name of the resource group.
  * publicIpAddressName **required** `string`: The name of the public IP address.
  * parameters **required** `object`: Tags object for patch operations.
    * tags `object`: Resource tags.
  * api-version **required** `string`: Client API version.
  * subscriptionId **required** `string`: The subscription credentials which uniquely identify the Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.

#### Output
* output [PublicIPAddress](#publicipaddress)

### PublicIPAddresses_CreateOrUpdate
Creates or updates a static or dynamic public IP address.


```js
azure_network_publicipaddress.PublicIPAddresses_CreateOrUpdate({
  "resourceGroupName": "",
  "publicIpAddressName": "",
  "parameters": null,
  "api-version": "",
  "subscriptionId": ""
}, context)
```

#### Input
* input `object`
  * resourceGroupName **required** `string`: The name of the resource group.
  * publicIpAddressName **required** `string`: The name of the public IP address.
  * parameters **required** [PublicIPAddress](#publicipaddress)
  * api-version **required** `string`: Client API version.
  * subscriptionId **required** `string`: The subscription credentials which uniquely identify the Microsoft Azure subscription. The subscription ID forms part of the URI for every service call.

#### Output
* output [PublicIPAddress](#publicipaddress)



## Definitions

### IpTag
* IpTag `object`: Contains the IpTag associated with the public IP address
  * ipTagType `string`: Gets or sets the ipTag type: Example FirstPartyUsage.
  * tag `string`: Gets or sets value of the IpTag associated with the public IP. Example SQL, Storage etc

### PublicIPAddress
* PublicIPAddress `object`: Public IP address resource.
  * etag `string`: A unique read-only string that changes whenever the resource is updated.
  * properties [PublicIPAddressPropertiesFormat](#publicipaddresspropertiesformat)
  * sku `object`: SKU of a public IP address
    * name `string` (values: Basic, Standard): Name of a public IP address SKU.
  * zones `array`: A list of availability zones denoting the IP allocated for the resource needs to come from.
    * items `string`
  * id `string`: Resource ID.
  * location `string`: Resource location.
  * name `string`: Resource name.
  * tags `object`: Resource tags.
  * type `string`: Resource type.

### PublicIPAddressDnsSettings
* PublicIPAddressDnsSettings `object`: Contains FQDN of the DNS record associated with the public IP address
  * domainNameLabel `string`: Gets or sets the Domain name label.The concatenation of the domain name label and the regionalized DNS zone make up the fully qualified domain name associated with the public IP address. If a domain name label is specified, an A DNS record is created for the public IP in the Microsoft Azure DNS system.
  * fqdn `string`: Gets the FQDN, Fully qualified domain name of the A DNS record associated with the public IP. This is the concatenation of the domainNameLabel and the regionalized DNS zone.
  * reverseFqdn `string`: Gets or Sets the Reverse FQDN. A user-visible, fully qualified domain name that resolves to this public IP address. If the reverseFqdn is specified, then a PTR DNS record is created pointing from the IP address in the in-addr.arpa domain to the reverse FQDN. 

### PublicIPAddressListResult
* PublicIPAddressListResult `object`: Response for ListPublicIpAddresses API service call.
  * nextLink `string`: The URL to get the next set of results.
  * value `array`: A list of public IP addresses that exists in a resource group.
    * items [PublicIPAddress](#publicipaddress)

### PublicIPAddressPropertiesFormat
* PublicIPAddressPropertiesFormat `object`: Public IP address properties.
  * dnsSettings `object`: Contains FQDN of the DNS record associated with the public IP address
    * domainNameLabel `string`: Gets or sets the Domain name label.The concatenation of the domain name label and the regionalized DNS zone make up the fully qualified domain name associated with the public IP address. If a domain name label is specified, an A DNS record is created for the public IP in the Microsoft Azure DNS system.
    * fqdn `string`: Gets the FQDN, Fully qualified domain name of the A DNS record associated with the public IP. This is the concatenation of the domainNameLabel and the regionalized DNS zone.
    * reverseFqdn `string`: Gets or Sets the Reverse FQDN. A user-visible, fully qualified domain name that resolves to this public IP address. If the reverseFqdn is specified, then a PTR DNS record is created pointing from the IP address in the in-addr.arpa domain to the reverse FQDN. 
  * idleTimeoutInMinutes `integer`: The idle timeout of the public IP address.
  * ipAddress `string`: The IP address associated with the public IP address resource.
  * ipConfiguration [./networkInterface.jsonIPConfiguration](#./networkinterface.jsonipconfiguration)
  * ipTags `array`: The list of tags associated with the public IP address.
    * items `object`: Contains the IpTag associated with the public IP address
      * ipTagType `string`: Gets or sets the ipTag type: Example FirstPartyUsage.
      * tag `string`: Gets or sets value of the IpTag associated with the public IP. Example SQL, Storage etc
  * provisioningState `string`: The provisioning state of the PublicIP resource. Possible values are: 'Updating', 'Deleting', and 'Failed'.
  * publicIPAddressVersion `string` (values: IPv4, IPv6): The public IP address version. Possible values are: 'IPv4' and 'IPv6'.
  * publicIPAllocationMethod `string` (values: Static, Dynamic): The public IP allocation method. Possible values are: 'Static' and 'Dynamic'.
  * resourceGuid `string`: The resource GUID property of the public IP resource.

### PublicIPAddressSku
* PublicIPAddressSku `object`: SKU of a public IP address
  * name `string` (values: Basic, Standard): Name of a public IP address SKU.


