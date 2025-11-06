# External Orders API

## Example post to create order
```
//use dev for testing purposes. use production when ready
const baseUrl = isDev ? "http://dev.gpsorders.com" : "http://gpsorders.com"; 

const options = {
  method: "POST",
  url: `${baseUrl}/api/orders/externalorder/create",
  headers: {
    "Content-Type": "application/json",
    "Access-Token": "5c23b2cf-6b02-411c-b3b2-6c223422fc6g", //the access token provided to the vendor by GPS. This is unique and should not be shared
  },
  body: JSON.stringify({
    orders: [ //an array of orders to create
      {
        order: {
          extId: "9384798749837498", //external id that external vendor would use to track the order
          orderType: "layover", // oneOf ["layover", "dropoff", "sameday"] | type: string
          pickupLN: "402-00001", //the vendor license number | type: string
          destinationLN: "313-00003", //the destination license number | type: string
          preferredDelivery: "2021-04-08T19:40:30.443Z", // the preferred delivery date | type: UTC date string
          preferredPickup: "2021-04-08T19:40:30.443Z", // optional - if provided it will use that date, otherwise it will use the preferred delivery date - 1 day | type: UTC date string
          weight: "5lbs", //optional | type: string
          notes: "Some notes",//optional | type: string
        },
        billing: { //optional - but likely needed for this datacann communication
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
      "id": "88a6be7d-eece-41c1-9d64-0b5b83752f22",
      "data": {
        "order": {
          "orderType": "layover",
          "pickupLN": "402-00001",
          "destinationLN": "402-00002",
          "preferredDelivery": "2024-07-17T19:52:56.513Z",
          "weight": "5lbs",
          "notes": "Some notes for test order",
          "status": 1,
          "dateApproved": "2024-07-10T22:34:31.251Z",
          "preferredPickup": "2024-07-16T06:00:00.000Z",
          "pickupDate": "2024-07-16T06:00:00.000Z",
          "pickupRoute": "{\"id\":\"007b613f-9579-4c34-a6fe-277299180eee\",\"parent\":\"007b613f-9579-4c34-a6fe-277299180eee\",\"name\":\"Denver West\",\"city\":\"Denver - Colfax/Speer\",\"zipCode\":\"80204\",\"day\":\"tue\"}",
          "driver": {
            "pickup": {
              "driver": {
                "name": "Jonathan Goddard",
                "phone": "(303) 472-3890",
                "lic": "14-231-0691",
                "email": "goddard92j@gmail.com",
                "occLic": "M20877"
              },
              "vehicle": {
                "name": "Ford Transit",
                "lic": "BSE-A35",
                "vin": null
              },
              "route": {
                "city": "Denver - Colfax/Speer",
                "zipCode": "80204",
                "day": "tue",
                "name": "Denver West"
              }
            },
            "delivery": {
              "driver": {
                "name": "Jose Lopez",
                "phone": "(720) 939-6029",
                "lic": "09-215-0651",
                "email": "lopezxxjose3@gmail.com",
                "occLic": "M56576"
              },
              "vehicle": {
                "name": "Ram Promaster",
                "lic": "AZQ-P53",
                "vin": null
              },
              "route": {
                "city": "Denver - City Park/Colfax",
                "zipCode": "80218",
                "day": "wed",
                "name": "Denver Central"
              }
            }
          },
          "deliveryDate": "2024-07-17T19:52:56.513Z",
          "route": "{\"id\":\"57af57e0-f8ae-4a3c-85a1-5b093dd6ef34\",\"parent\":\"57af57e0-f8ae-4a3c-85a1-5b093dd6ef34\",\"name\":\"Denver Central\",\"city\":\"Denver - City Park/Colfax\",\"zipCode\":\"80218\",\"day\":\"wed\"}"
        },
        "ext": {
          "name": "Distru",
          "userId": "d0102ab8-81ed-4eb0-ab98-5d26ee3906fd",
          "approve": true,
          "id": "9384798749837498"
        },
        "destCompany": {
          "Street Address": "1301 North Marion Street",
          "Licensee": "ALTERNATIVE MEDICINE ON CAPITOL HILL LLC ",
          "License #": "402-00002",
          "DBA": "",
          "FacilityType": "MMC",
          "City": "Denver",
          "Zip": "80218",
          "DateUpdated": "2022-07-01",
          "profession_id": "Marijuana Enforcement",
          "license_type": "Center - Type 1",
          "sec_lic_status": "Approved",
          "addr_line_2": "",
          "addr_line_4": "Denver CO  80218",
          "addr_county": "Denver",
          "addr_state": "CO",
          "field13": ""
        },
        "pickupCompany": {
          "Street Address": "762 North Kalamath Street",
          "Licensee": "ALLGREENS LLC",
          "License #": "402-00001",
          "DBA": "",
          "FacilityType": "MMC",
          "City": "Denver",
          "Zip": "80204",
          "DateUpdated": "2022-07-01",
          "profession_id": "Marijuana Enforcement",
          "license_type": "Center - Type 1",
          "sec_lic_status": "Approved",
          "addr_line_2": "",
          "addr_line_4": "Denver CO  80204",
          "addr_county": "Denver",
          "addr_state": "CO",
          "field13": ""
        }
      },
      "userId": "d0102ab8-81ed-4eb0-ab98-5d26ee3906fd",
      "orderId": "402-00001-EXT-8",
      "created": "2024-07-10T22:34:33.669Z",
      "lastUpdated": "2024-07-10T22:34:33.669Z"
    }
  ]
}

```
This is the example response that is returned from our api. The client can use this information to update their records accordingly. The "id" is the unique identifier and is more reliable then the "orderId".

## Example post to update order (This endpoint is in place, but not fully configured. Only response you will get is {  success: true })
```
//use dev for testing purposes. use production when ready
const baseUrl = isDev ? "http://dev.gpsorders.com" : "http://gpsorders.com"; 

const options = {
  method: "POST",
  url: `${baseUrl}/api/orders/externalorder/update",
  headers: {
    "Content-Type": "application/json",
    "Access-Token": "5c23b2cf-6b02-411c-b3b2-6c223422fc6g", //the access token provided to the vendor by GPS. This is unique and should not be shared
  },
  body: JSON.stringify({
    orders: [ //an array of orders to create
      {
        order: {
          extId: "9384798749837498", //external id that external vendor would use to track the order
          orderType: "layover", // oneOf ["layover", "dropoff", "sameday"] | type: string
          pickupLN: "402-00001", //the vendor license number | type: string
          destinationLN: "313-00003", //the destination license number | type: string
          preferredDelivery: "2021-04-08T19:40:30.443Z", // the preferred delivery date | type: UTC date string
          preferredPickup: "2021-04-08T19:40:30.443Z", // optional - if provided it will use that date, otherwise it will use the preferred delivery date - 1 day | type: UTC date string
          weight: "5lbs", //optional | type: string
          notes: "Some notes",//optional | type: string
        },
        billing: { //optional - but likely needed for this datacann communication
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

The response should be very similar to above (when this endpoint is fully configured)

## Example to get the latest information from an order
```
//use dev for testing purposes. use production when ready
const baseUrl = isDev ? "http://dev.gpsorders.com" : "http://gpsorders.com"; 

const options = {
  method: "GET",
  url: `${baseUrl}/api/orders/externalorder/orderid/403R-00467-5",
  headers: {
    "Content-Type": "application/json",
    "Access-Token": "5c23b2cf-6b02-411c-b3b2-6c223422fc6g", //the access token provided to the vendor by GPS. This is unique and should not be shared
  }
};
```

Example Response
```
{
  "orders": [
    {
      "id": "ea7b46fd-be8c-45c2-95be-bbfa1f224147",
      "userId": "a3647cc3-fcb2-4fdc-8564-56ad13177681",
      "data": {
        "ext": {
          "name": "Greenlists",
          "userId": "a3647cc3-fcb2-4fdc-8564-56ad13177681",
          "approve": true,
          "id": "EXTERNALID"
        },
        "billing": {
          "amount": "bill amount",
          "invoice": "GL Order #424",
          "method": "billing method",
          "manifest": "transfer template created"
        },
        "order": {
          "orderType": "layover",
          "pickupLN": "403R-00467",
          "destinationLN": "403R-00953",
          "preferredPickup": "2025-10-27T00:00:00.000Z",
          "preferredDelivery": "2025-10-29T00:00:00+00:00",
          "weight": 0,
          "notes": "GL Order #424",
          "pickupType": "layoverpickup",
          "driver": {},
          "status": "RECEIVED"
        },
        "destCompany": {
          "Street Address": "60800 Highway 96 East",
          "Licensee": "ANGEL FARMS LLC",
          "License #": "403R-00953",
          "DBA": "None",
          "FacilityType": "Retail Marijuana Cultivation Facility",
          "City": "Boone",
          "Zip": "81025",
          "DateUpdated": "2025-10-01"
        },
        "pickupCompany": {
          "Street Address": "60710 Highway 96 East",
          "Licensee": "BOONE FARMS LLC",
          "License #": "403R-00467",
          "DBA": "None",
          "FacilityType": "Retail Marijuana Cultivation Facility",
          "City": "Boone",
          "Zip": "81025",
          "DateUpdated": "2025-10-01"
        }
      },
      "deleted": 0,
      "orderId": "403R-00467-GREENLISTS-5",
      "created": "2025-10-22T04:49:31.961Z",
      "lastUpdated": "2025-10-22T04:49:31.961Z",
      "deliveryDate": null
    }
  ]
}
```

## Status's
The status keys. External orders will receive the status value that is listed in the "var" key shown below, ie `RECEIVED`
```
const deliveryStatus = [
  { title: 'Order Received', value: OrderStatus.orderReceived, color: colors.error, var: 'RECEIVED' },
  { title: 'Order Approved', value: OrderStatus.orderApproved, color: colors.warning, var: 'APPROVED' },
  { title: 'Order Picked Up', value: OrderStatus.orderPickedUp, color: colors.success, var: 'PICKED_UP' },
  { title: 'In Transit', value: OrderStatus.inTransit, color: colors.warning, var: 'IN_TRANSIT' },
  { title: 'Delivered', value: OrderStatus.delivered, color: colors.success, var: 'DELIVERED' },
  { title: 'Exception', value: OrderStatus.exception, color: colors.warning, var: 'EXCEPTION' },
  { title: 'Full Rejection', value: OrderStatus.fullrejection, color: colors.error, var: 'REJECTION' },
  { title: 'Partial Rejection', value: OrderStatus.partialrejection, color: colors.error, var: 'REJECTION_PARTIAL' },
  { title: 'Order Cancelled', value: OrderStatus.orderCancelled, color: colors.error, var: 'CANCELLED' },
]
```

## Manifest Date Values
These are the values we use from our orders to fill out the manifest datetimes
```
destination.EstimatedDepartureDateTime = data.order.pickupDate
destination.EstimatedArrivalDateTime = data.order.deliveryDate

transporter.EstimatedDepartureDateTime = data.order.deliveryDate
transporter.EstimatedArrivalDateTime = data.order.pickupDate
```