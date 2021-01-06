![version](https://img.shields.io/badge/version-1.0.0-brightgreen.svg?style=flat-square)

# Matooma API documentation

Version   | Date
--------- | --------------
**[1.0.0](#-Version-1-0-0)** | **11-01-2021**

# Version 1.0.0

1. [Authentication](#-authentication)
2. [Consumptions](#-consumptions)
3. [Devices](#-devices)
4. [Agencies](#-agencies)
5. [Manufacturers](#-manufacturers)
6. [Offers](#-offers)
7. [Operators](#-operators)
8. [Pairing](#-pairing)
9. [Profiles](#-profiles)
10. [Provisioning](#-provisioning)
11. [Simcards](#-simcards)
12. [SMS](#-sms)

## :warning: Major updates

* Remove route Manufacturers (_/v1/manufacturers_)
* Remove route Profiles (_/v1/profiles_) to route Offers (_/v1/offers_)
* Update route Offers (_/v1/offers_)
* Remove attribute **manufacturer** of every route
* Remove attribute **profileId** of every route
* Remove query parameter linked to Manufacturers
* Remove query parameter linked to Profiles
* Add a new level _customer_ on multiple entities
* The level agency is now replaced by the new level customer. The level agency remains as a sub-level of a customer (a customer may have multiple agencies).
* An agency always depends on and is always linked to a customer.

## Update details

### Authentication

> <span style="color: #009D77">**POST**</span> /v1/token
* N/A

-------------------------------

### Consumptions
> <span style="color: #1391FF">**GET**</span> /v1/consumptions/daily/{iccid}
* N/A

> <span style="color: #1391FF">**GET**</span> /v1/consumptions/total/{iccid}
* N/A

-------------------------------

### Devices
> <span style="color: #1391FF">**GET**</span> /v1/devices

* Change of the attribute _profileName_ to _offerName_
* Add a new attribute _customer_ of type objet with two attributes: _id_ and _name_

<table>
    <thead>
        <tr>
            <th>Previous payload</th>
            <th>New payload</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<pre>
[
  {
    "id": 1,
    "reference": "12345",
    "contractNumber": "123456",
    "serialNumber": "123456",
    "apn": "m2minternet",
    "gsmData": null,
    "comment": "",
    "imei": "",
    "msisdn": "+33xxxxxxxxx",
    "profileName": "DATA XXX Ko X SMS Voix Entrante XXX",
    "isMatoowan": true,
    "simcardIccid": "XXXXXXXXXXXXXXXXXXXX",
    "simcardState": "active",
    "simcardVersion": "v1",
    "operatorSlug": "XXX",
    "agency": {
      "id": 2,
      "name": "Agency 2"
    },
    "modelId": 1234,
    "modelName": "Device Model name",
    "manufacturerName": "Manufacturer name",
    "simcardActivationDate": "XXXX-XX-XX XX:XX:XX",
    "simcardTerminationDate": null,
    "networkIp": null,
    "networkLogin": null,
    "networkPassword": null,
    "history": [],
    "sms": {
      "in": [],
      "out": []
    }
  }
]
</pre>
            </td>
            <td>
<pre>
[
  {
    "id": 1,
    "reference": "12345",
    "contractNumber": "123456",
    "serialNumber": "123456",
    "apn": "m2minternet",
    "gsmData": null,
    "comment": "Comment",
    "imei": "000111222",
    "msisdn": "+33000000000",
    "offerName": "DATA XXX Ko X SMS Voix Entrante XXX",
    "simcardIccid": "01234567890123456789",
    "simcardState": "active",
    "simcardVersion": "v1",
    "isMatoowan": false,
    "operatorSlug": "Operator 1",
    "customer": {
      "id": 1,
      "name": "Customer 1"
    },
    "agency": {
      "id": 2,
      "name": "Agency 2"
    },
    "modelId": 1234,
    "modelName": "Device Model name",
    "manufacturerName": "Manufacturer name",
    "simcardActivationDate": "2021-01-01 00:00:00",
    "simcardTerminationDate": null,
    "networkIp": null,
    "networkLogin": null,
    "networkPassword": null,
    "history": [],
    "sms": {
      "in": [],
      "out": []
    }
  }
]
</pre>
            </td>
        </tr>
    </tbody>
</table>

> <span style="color: #1391FF">**GET**</span> /v1/devices/{id}

* Change of the attribute _profileName_ to _offerName_
* Add a new attribute _customer_ of type objet with two attributes: _id_ and _name_

<table>
    <thead>
        <tr>
            <th>Previous payload</th>
            <th>New payload</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<pre>
  {
    "id": 1,
    "reference": "12345",
    "contractNumber": "123456",
    "serialNumber": "123456",
    "apn": "m2minternet",
    "gsmData": null,
    "comment": "",
    "imei": "",
    "msisdn": "+33xxxxxxxxx",
    "profileName": "DATA XXX Ko X SMS Voix Entrante XXX",
    "isMatoowan": false,
    "simcardIccid": "XXXXXXXXXXXXXXXXXXXX",
    "simcardState": "active",
    "simcardVersion": "v1",
    "operatorSlug": "XXX",
    "agency": {
      "id": 2,
      "name": "Agency 2"
    },
    "modelId": 1234,
    "modelName": "Device Model name",
    "manufacturerName": "Manufacturer name",
    "simcardActivationDate": "XXXX-XX-XX XX:XX:XX",
    "simcardTerminationDate": null,
    "networkIp": null,
    "networkLogin": null,
    "networkPassword": null,
    "history": [],
    "sms": {
      "in": [],
      "out": []
    }
  }
</pre>
            </td>
            <td>
<pre>
  {
    "id": 1,
    "reference": "12345",
    "contractNumber": "123456",
    "serialNumber": "123456",
    "apn": "m2minternet",
    "gsmData": null,
    "comment": "Comment",
    "imei": "000111222",
    "msisdn": "+33000000000",
    "offerName": "DATA XXX Ko X SMS Voix Entrante XXX",
    "isMatoowan": false,
    "simcardIccid": "01234567890123456789",
    "simcardState": "active",
    "simcardVersion": "v1",
    "operatorSlug": "Operator 1",
    "customer": {
      "id": 1,
      "name": "Customer 1"
    },
    "agency": {
      "id": 2,
      "name": "Agency 2"
    },
    "modelId": 1234,
    "modelName": "Device Model name",
    "manufacturerName": "Manufacturer name",
    "simcardActivationDate": "2021-01-01 00:00:00",
    "simcardTerminationDate": null,
    "networkIp": null,
    "networkLogin": null,
    "networkPassword": null,
    "history": [],
    "sms": {
      "in": [],
      "out": []
    }
  }
</pre>
            </td>
        </tr>
    </tbody>
</table>

> <span style="color: #00A0A7">**PATCH**</span> /v1/devices/{id}

* N/A

> <span style="color: #1391FF">**GET**</span> /v1/devices/models

* Deletion of the query parameter _operatorSlug_ as a device model does not depend on a specific operator
* Add of a new query parameter _customerId_ to filter on a specific customer identifier

-------------------------------

### Agencies
> <span style="color: #1391FF">**GET**</span> /v1/agencies

* The level agency is now replaced by the new level customer. The level agency remains as a sub-level of a customer (a customer may have multiple agencies).
* An agency always depends on and is always linked to a customer.
* Deletion of attribute _default_

<table>
    <thead>
        <tr>
            <th>Previous payload</th>
            <th>New payload</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<pre>
[
  {
    "default": false,
    "id": "1",
    "name": "My agency"
  }
]
</pre>
            </td>
            <td>
<pre>
[
  {
    "id": 1,
    "name": "My agency"
  }
]
</pre>
            </td>
        </tr>
    </tbody>
</table>

-------------------------------

### Manufacturers
> <span style="color: #1391FF">**GET**</span> ~~/v1/manufacturers~~

* Deletion of this route with no replacement

-------------------------------

### Offers
> <span style="color: #1391FF">**GET**</span> /v1/offers

* Deletion of the query parameter _agencyId_ as an offer does not depend on a specific agency anymore but on a specific customer
* Deletion of the query parameter _deviceModelId_ as an offer does not depend on a specific device model anymore
* Add of a new query parameter _customerId_ as replacement of the query parameter _agencyId_ to filter on a specific customer identifier
* Deletion of the attribute _profileId_ as an offer does not depend on a profile anymore
* Deletion of the attribute _agencyId_ as an offer does not depend on an agency anymore
* Deletion of the attribute _agencyName_ as an offer does not depend on an agency anymore
* Add a new attribute _customer_ of type objet with two attributes: _id_ and _name_

<table>
    <thead>
        <tr>
            <th>Previous payload</th>
            <th>New payload</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<pre>
[
  {
    "id": 2,
    "profileId": 5,
    "name": "DATA 500 Ko",
    "agencyId": 2,
    "agencyName": "My Agency 2"
  }
]
</pre>
            </td>
            <td>
<pre>
[
  {
    "id": 2,
    "name": "DATA 500 Ko",
    "customer": {
      "id": 2,
      "name": "Customer 2"
    }
  }
]
</pre>
            </td>
        </tr>
    </tbody>
</table>

> <span style="color: #1391FF">**GET**</span> /v1/offers/{id}

* Deletion of the attribute _profileId_ as an offer does not depend on a profile anymore
* Deletion of the attribute _agencyId_ as an offer does not depend on an agency anymore
* Deletion of the attribute _agencyName_ as an offer does not depend on an agency anymore
* Add a new attribute _customer_ of type objet with two attributes: _id_ and _name_

<table>
    <thead>
        <tr>
            <th>Previous payload</th>
            <th>New payload</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<pre>
  {
    "id": 2,
    "profileId": 5,
    "name": "DATA 500 Ko",
    "agencyId": 2,
    "agencyName": "My Agency 2"
  }
</pre>
            </td>
            <td>
<pre>
  {
    "id": 2,
    "name": "DATA 500 Ko",
    "customer": {
      "id": 2,
      "name": "Customer 2"
    }
  }
</pre>
            </td>
        </tr>
    </tbody>
</table>

-------------------------------

### Operators
> <span style="color: #1391FF">**GET**</span> /v1/operators

* Deletion of the query parameter _agencyId_ as an operator does not depend on a specific agency anymore
* Deletion of the query parameter _manufacturerId_ as an operator does not depend on a specific manufacturer anymore

-------------------------------

### Pairing
> <span style="color: #009D77">**POST**</span> /v1/pairing

* Deletion of the attribute _templateId_
* Deletion of the attribute _manufacturerId_
* Deletion of the attribute _operatorSlug_
* Change the name of the attribute _profileId_ to _offerId_
* Deletion of the attributes _serialNumber_, _reference_, _imei_ and _comment_ of the attribute _items_ (they won't be used if they are still present)
* Add of a new attribute _customerId_ of type integer

<table>
    <thead>
        <tr>
            <th>Previous payload</th>
            <th>New payload</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<pre>
{
  "dry-run": true,
  "agencyId": "XXX",
  "manufacturerId": "XXX",
  "operatorSlug": "XXX",
  "modelId": "XXX",
  "profileId": "XXX",
  "items": [
    {
      "iccid": "XXXXXXXXXXXXXXXXXXXX",
      "serialNumber": "XXXXXXXXXXXXXXXXXXXX",
      "reference": "XXXXXXXXXXXXXXXXXXXX",
      "imei": "XXXXXXXXXXXXXXXXXXXX",
      "comment": "XXXXXXXXXXXXXXXXXXXX"
    }
  ]
}
</pre>
            </td>
            <td>
<pre>
{
  "dry-run": true,
  "customerId": 1,
  "agencyId": 2,
  "modelId": 3,
  "offerId": 4,
  "items": [
    "01234567890123456789",
    "12345678901234567890"
  ]
}
</pre>
            </td>
        </tr>
    </tbody>
</table>

* Add the return code _400_ if the offer does not exist for the given couple customer/agency or if the offer is not compatible with the given device model

<table>
    <thead>
        <tr>
            <th>Previous payload</th>
            <th>New payload</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<pre>
None
</pre>
            </td>
            <td>
<pre>
{
  "code": "400,",
  "message": "The offer 1 doesn't have any rattachement for customer Customer 1 and agency 1"
}
</pre>
            </td>
            <td>
            </td>
        </tr>
        <tr>
            <td>
<pre>
None
</pre>
            </td>
            <td>
<pre>
{
  "code": "400,",
  "message": "Sim Card Offer Not Compatible With Device Model"
}
</pre>
            </td>
        </tr>
    </tbody>
</table>

> <span style="color: #1391FF">**GET**</span> /v1/pairing/templates

* Deletion of the attribute _manufacturer_
* Change of the attribute name _profile_ to the attribute _offer_ with the same attributes
* Add a new attribute _customer_ of type objet with two attributes: _id_ and _name_

<table>
    <thead>
        <tr>
            <th>Previous payload</th>
            <th>New payload</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<pre>
[
  {
    "id": "XXXX",
    "label": "XXXX",
    "agency": {
      "agencyId": "XXXX",
      "agencyName": "XXXX"
    },
    "profile": {
      "profileId": "XXXX",
      "profileName": "XXXX"
    },
    "model": {
      "modelId": "XXXX",
      "modelName": "XXXX"
    },
    "manufacturer": {
      "manufacturerId": "XXXX",
      "manufacturerName": "XXXX"
    },
    "operatorSlug": "XXXX"
  }
]
</pre>
            </td>
            <td>
<pre>
[
  {
    "id": "1",
    "label": "Pairing template",
    "customer": {
      "id": 1,
      "name": "Customer 1"
    },
    "agency": {
      "id": 2,
      "name": "Agency 2"
    },
    "offer": {
      "id": 3,
      "name": "Offer 3"
    },
    "model": {
      "id": 4,
      "name": "Model 4"
    },
    "operatorSlug": "Operator"
  }
]
</pre>
            </td>
        </tr>
    </tbody>
</table>

> <span style="color: #009D77">**POST**</span> /v1/pairing/templates

* Deletion of the attribute _manufacturerId_
* Change of the attribute name _profile_ to the attribute _offer_ with the same attributes _id_ and _name_
* Add a new attribute _customerId_ of type integer

<table>
    <thead>
        <tr>
            <th>Previous payload</th>
            <th>New payload</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<pre>
{
  "label": "XXXXX",
  "agencyId": "XXXXX",
  "manufacturerId": "XXXXX",
  "operatorSlug": "XXXXX",
  "modelId": "XXXXX",
  "profileId": "XXXXX"
}
</pre>
            </td>
            <td>
<pre>
{
  "label": "Label",
  "customerId": 1,
  "agencyId": 2,
  "offerId": 3,
  "modelId": 4,
  "operatorSlug": "Operator"
}
</pre>
            </td>
        </tr>
    </tbody>
</table>

> <span style="color: #1391FF">**GET**</span> /v1/pairing/templates/{id}

* Deletion of the attribute _manufacturer_
* Change of the attribute name _profile_ to the attribute _offer_ with the same attributes _id_ and _name_
* Add a new attribute _customer_ of type objet with two attributes: _id_ and _name_

<table>
    <thead>
        <tr>
            <th>Previous payload</th>
            <th>New payload</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<pre>
  {
    "id": "XXXX",
    "label": "XXXX",
    "agency": {
      "agencyId": "XXXX",
      "agencyName": "XXXX"
    },
    "profile": {
      "profileId": "XXXX",
      "profileName": "XXXX"
    },
    "model": {
      "modelId": "XXXX",
      "modelName": "XXXX"
    },
    "manufacturer": {
      "manufacturerId": "XXXX",
      "manufacturerName": "XXXX"
    },
    "operatorSlug": "XXXX"
  }
</pre>
            </td>
            <td>
<pre>
  {
    "id": "1",
    "label": "Pairing template",
    "customer": {
      "id": 1,
      "name": "Customer 1"
    },
    "agency": {
      "id": 2,
      "name": "Agency 2"
    },
    "offer": {
      "id": 3,
      "name": "Offer 3"
    },
    "model": {
      "id": 4,
      "name": "Model 4"
    },
    "operatorSlug": "Operator"
  }
</pre>
            </td>
        </tr>
    </tbody>
</table>

> <span style="color: #00A0A7">**PATCH**</span> /v1/pairing/templates/{id}

* N/A

> <span style="color: #CF3030">**DELETE**</span> /v1/pairing/templates/{id}

* N/A

-------------------------------

### Profiles
> <span style="color: #1391FF">**GET**</span> ~~/v1/profiles~~
* Deletion of this route with no replacement

-------------------------------

### Provisioning
> <span style="color: #009D77">**POST**</span> /v1/provisioning-requests

* Add the missing action _reactivate_ in documentation

> <span style="color: #1391FF">**GET**</span> /v1/provisioning-requests

* Add the missing action _reactivate_ in documentation
* Add a new attribute _requestedForCustomer_ of type string
* Add a new attribute _createdByCustomer_ of type object with two attributes _id_ and _name_

<table>
    <thead>
        <tr>
            <th>Previous payload</th>
            <th>New payload</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<pre>
[
  {
    "id": 1234,
    "agencyName": "My Agency",
    "user": "Me",
    "status": "done",
    "action": "activate",
    "createdAt": "XXXX-XX-XX XX:XX:XX",
    "items": {
      "1234": {
        "id": 1234,
        "iccid": "XXXXXXXXXXXXXXXXXXXX",
        "requestAt": "XXXX-XX-XX XX:XX:XX",
        "status": "done",
        "requestedForAgency": "My Agency",
        "operatorSlug": "XXX",
        "processingDate": "XXXX-XX-XX XX:XX:XX"
      }
    },
    "createdByAgency": {
      "id": 1,
      "name": "My Agency"
    },
    "createdByUser": {
      "id": 1,
      "name": "Me"
    }
  }
]
</pre>
            </td>
            <td>
<pre>
[
  {
    "id": 1234,
    "agencyName": "My Agency",
    "user": "Me",
    "status": "done",
    "action": "activate",
    "createdAt": "2021-01-01 00:00:00",
    "items": [
      {
        "id": 1234,
        "iccid": "01234567890123456789",
        "requestAt": "2021-01-01 00:00:00",
        "status": "done",
        "requestedForCustomer": "My Customer",
        "requestedForAgency": "My Agency",
        "operatorSlug": "Operator 1",
        "processingDate": "2021-01-01 00:00:00"
      }
    ],
    "createdByCustomer": {
      "id": 1,
      "name": "My Customer"
    },
    "createdByAgency": {
      "id": 1,
      "name": "My Agency"
    },
    "createdByUser": {
      "id": 1,
      "name": "Me"
    }
  }
]
</pre>
            </td>
        </tr>
    </tbody>
</table>

> <span style="color: #1391FF">**GET**</span> /v1/provisioning-requests/{id}

* Add of the missing action _reactivate_ in documentation
* Add a new attribute _requestedForCustomer_ of type string
* Add a new attribute _createdByCustomer_ of type object with two attributes _id_ and _name_

<table>
    <thead>
        <tr>
            <th>Previous payload</th>
            <th>New payload</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<pre>
  {
    "id": 1234,
    "agencyName": "My Agency",
    "user": "Me",
    "status": "done",
    "action": "activate",
    "createdAt": "XXXX-XX-XX XX:XX:XX",
    "items": {
      "1234": {
        "id": 1234,
        "iccid": "XXXXXXXXXXXXXXXXXXXX",
        "requestAt": "XXXX-XX-XX XX:XX:XX",
        "status": "done",
        "requestedForAgency": "My Agency",
        "operatorSlug": "XXX",
        "processingDate": "XXXX-XX-XX XX:XX:XX"
      }
    },
    "createdByAgency": {
      "id": 1,
      "name": "My Agency"
    },
    "createdByUser": {
      "id": 1,
      "name": "Me"
    }
  }
</pre>
            </td>
            <td>
<pre>
  {
    "id": 1234,
    "agencyName": "My Agency",
    "user": "Me",
    "status": "done",
    "action": "activate",
    "createdAt": "2021-01-01 00:00:00",
    "items": [
      {
        "id": 1234,
        "iccid": "01234567890123456789",
        "requestAt": "2021-01-01 00:00:00",
        "status": "done",
        "requestedForCustomer": "My Customer",
        "requestedForAgency": "My Agency",
        "operatorSlug": "Operator 1",
        "processingDate": "2021-01-01 00:00:00"
      }
    ],
    "createdByCustomer": {
      "id": 1,
      "name": "My Customer"
    },
    "createdByAgency": {
      "id": 1,
      "name": "My Agency"
    },
    "createdByUser": {
      "id": 1,
      "name": "Me"
    }
  }
</pre>
            </td>
        </tr>
    </tbody>
</table>

-------------------------------

### Simcards
> <span style="color: #1391FF">**GET**</span> /v1/simcards

* Add a new attribute _customer_ of type object with two attributes _id_ and _name_

<table>
    <thead>
        <tr>
            <th>Previous payload</th>
            <th>New payload</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<pre>
[
  {
    "id": 1,
    "agency": {
      "agencyId": 2,
      "agencyName": "My Agency 2"
    },
    "deviceId": 1,
    "simcardState": "in-stock",
    "simcardIccid": "XXXXXXXXXXXXXXXXXXXX",
    "simcardVersion": "sav",
    "operatorSlug": "orange",
    "simcardOrderId": 1,
    "simcardOrderDate": "XXXX-XX-XX XX:XX:XX",
    "orderedBy": "Me",
    "simcardRequest": null
  }
]
</pre>
            </td>
            <td>
<pre>
[
  {
    "id": 1,
    "customer": {
      "id": 2,
      "name": "My Customer 2"
    },
    "agency": {
      "id": 2,
      "name": "My Agency 2"
    },
    "deviceId": 1,
    "simcardState": "in-stock",
    "simcardIccid": "01234567890123456789",
    "simcardVersion": "sav",
    "operatorSlug": "orange",
    "simcardOrderId": 1,
    "simcardOrderDate": "2021-01-01 00:00:00",
    "orderedBy": "John Doe",
    "simcardRequest": 123456
  }
]
</pre>
            </td>
        </tr>
    </tbody>
</table>

> <span style="color: #1391FF">**GET**</span> /v1/simcards/{id}

* Add a new attribute _customer_ of type object with two attributes _id_ and _name_

<table>
    <thead>
        <tr>
            <th>Previous payload</th>
            <th>New payload</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
<pre>
  {
    "id": 1,
    "agency": {
      "agencyId": 2,
      "agencyName": "My Agency 2"
    },
    "deviceId": 1,
    "simcardState": "in-stock",
    "simcardIccid": "XXXXXXXXXXXXXXXXXXXX",
    "simcardVersion": "sav",
    "operatorSlug": "orange",
    "simcardOrderId": 1,
    "simcardOrderDate": "XXXX-XX-XX XX:XX:XX",
    "orderedBy": "Me",
    "simcardRequest": null
  }
</pre>
            </td>
            <td>
<pre>
  {
    "id": 1,
    "customer": {
      "id": 2,
      "name": "My Customer 2"
    },
    "agency": {
      "id": 2,
      "name": "My Agency 2"
    },
    "deviceId": 1,
    "simcardState": "in-stock",
    "simcardIccid": "01234567890123456789",
    "simcardVersion": "sav",
    "operatorSlug": "orange",
    "simcardOrderId": 1,
    "simcardOrderDate": "2021-01-01 00:00:00",
    "orderedBy": "John Doe",
    "simcardRequest": 123456
  }
</pre>
            </td>
        </tr>
    </tbody>
</table>

-------------------------------

### SMS
> <span style="color: #009D77">**POST**</span> /v1/sms

* Deletion of return code 200 as it was never used
