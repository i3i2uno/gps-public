# External Orders API

## Example post
```
//use dev for testing purposes. use production when ready
const baseUrl = "http://gps-env-dev.us-west-2.elasticbeanstalk.com"; 

const options = {
  method: "POST",
  url: `${baseUrl}/api/externalorders/create`,
  headers: {
    "Content-Type": "application/json",
    "Access-Token": "5c23b2cf-6b02-411c-b3b2-6c223422fc6g", //the access token provided to the vendor by GPS. This is unique and should not be shared
  },
  body: JSON.stringify({
    orders: [ //an array of orders to create
      {
        order: {
          orderType: "layover", // oneOf ["layover", "dropoff", "sameday"] | type: string
          pickupLN: "402-00001", //the vendor license number | type: string
          destinationLN: "313-00003", //the destination license number | type: string
          preferredDelivery: "2021-04-08T19:40:30.443Z", // the preferred delivery date | type: UTC date string
          weight: "5lbs", //optional | type: string
          notes: "Some notes",//optional | type: string
        },
        billing: { //optional
          amount: "bill amount", | type: string
          invoice: "invoice #", | type: string
          method: "billing method", | type: string
          manifest: "manifest number", | type: string
        },
      },
    ],
  }),
};
```
This post will be done by the vendors side, to our api using their unique access_token. This access token is connected to a users/clients account information and validates that their post is allowed to access our api.

## Example Response
```
{
  "createdOrders": [
    {
      "id": "b9b01aad-e57d-4121-a322-1df5d8a7e659",
      "data": {
        "order": {
          "orderType": "layover",
          "pickupLN": "402-00001",
          "destinationLN": "313-00003",
          "preferredDelivery": "2021-04-08T19:40:30.443Z",
          "weight": "5lbs",
          "notes": "Some notes"
        },
        "billing": {
          "amount": "bill amount",
          "invoice": "invoice #",
          "method": "billing method",
          "manifest": "manifest number"
        },
        "destCompany": {
          "profession_id": "Marijuana Enforcement",
          "license_type": "Transition Permit",
          "sec_lic_status": "Approved",
          "addr_line_2": "",
          "addr_line_4": "Fort Collins CO  80524",
          "addr_county": "Larimer",
          "addr_state": "CO",
          "field13": "",
          "Zip": "80524",
          "City": "Fort Collins",
          "License #": "313-00003",
          "Licensee": "LIVWELL VII LLC",
          "DBA": "LIVWELL VII LLC",
          "Street Address": "900 North College Avenue"
        },
        "pickupCompany": {
          "profession_id": "Marijuana Enforcement",
          "license_type": "Center - Type 1",
          "sec_lic_status": "Approved",
          "addr_line_2": "",
          "addr_line_4": "Denver CO  80204",
          "addr_county": "Denver",
          "addr_state": "CO",
          "field13": "",
          "Zip": "80204",
          "City": "Denver",
          "License #": "402-00001",
          "Licensee": "ALLGREENS LLC",
          "DBA": "ALLGREENS LLC",
          "Street Address": "762 North Kalamath Street"
        }
      },
      "userId": "d6ffa6c8-d392-9cc1-3d67-9600ce15f00b",
      "orderId": "402-00001-14",
      "created": "2021-05-16T17:57:18.181Z",
      "lastUpdated": "2021-05-16T17:57:18.181Z"
    }
  ]
}
```
This is the example response that is returned from our api. The client can use this information to update their records accordingly. The "id" is the unique identifier and is more reliable then the "orderId".
