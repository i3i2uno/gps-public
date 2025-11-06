# Schedule Output

## Example post to get schedule
```
//use dev for testing purposes. use production when ready
const baseUrl = isDev ? "http://dev.gpsorders.com" : "https://gpsorders.com"; 

const options = {
  method: "POST",
  url: `${baseUrl}/api/driverschedule/output",
  headers: {
    "Content-Type": "application/json",
    "Authorization": "5c23b2cf-6b02-411c-b3b2-6c223422fc6g", //the access token provided to the vendor by GPS. This is unique and should not be shared
  },
  body: JSON.stringify({
    "date": "2025-03-16T00:00:00.000Z" //this is a UTC date referencing the start of the week, ie sunday.
  }),
};
```

## Example response
You will receive a response like the following, with 1 = Monday, 2 = Tuesday, etc...
```
{
    "data": {
        "1": [
            {
                "driver": {
                    "id": "9cbbc27a-8237-4c43-b625-243b94a1f4fb",
                    "name": "Lukas Mazurek",
                    "phone": "(720) 757-3801",
                    "email": "lmazurek123456@gmail.com",
                    "lic": "17-131-5949",
                    "created": "2021-12-17T18:15:13.871Z",
                    "lastUpdated": "2024-05-10T15:17:07.379Z",
                    "occLic": "M112100"
                },
                "vehicle": {
                    "id": "9e225eb9-55a4-43cf-87d3-79b8680a73f7",
                    "name": "Hyundai Entourage",
                    "lic": "OSP-011",
                    "created": "2021-06-21T10:50:13.214Z",
                    "lastUpdated": "2024-07-30T15:31:39.136Z",
                    "data": {
                        "regpaperwork": "9f4af057-3d21-4765-85d6-0f6756521871_2024-07-30T15:27:51.744Z.pdf",
                        "reg_exp": "December 2024",
                        "insurance": "fca18367-d682-49f5-9908-6d947c45569b_2024-07-30T15:28:08.059Z.pdf",
                        "tiresize": "225 70R16",
                        "mileage_loc": 260741,
                        "mileage_tirechange": 245632,
                        "mileage_brakes": 245632,
                        "wintertires": 1,
                        "spare": 1,
                        "chains": 1,
                        "camera": 1,
                        "alarm": 1,
                        "radius": "long",
                        "ownerstatus": "owned",
                        "notes": "BEAST OF A VEHICLE"
                    },
                    "vin": "4290061941219001",
                    "year": "2007",
                    "mileage": "260741",
                    "status": 1
                },
                "route": {
                    "id": "57af57e0-f8ae-4a3c-85a1-5b093dd6ef34",
                    "name": "Denver Central",
                    "data": {
                        "rows": [
                            {
                                "id": "d7166149-4117-46c4-aee2-2abe9258496d",
                                "city": "Denver - North Denver/RiNo/Along I-25 & I-70",
                                "zipCode": "80216",
                                "dayOfTheWeek": [
                                    "mon",
                                    "tue",
                                    "wed",
                                    "thur",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "20.00"
                            },
                            {
                                "id": "0706812e-4c9e-4f6b-8d68-9c49e61ab65b",
                                "city": "Denver - Ballpark/Five Points/City Park",
                                "zipCode": "80205",
                                "dayOfTheWeek": [
                                    "mon",
                                    "tue",
                                    "wed",
                                    "thur",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "20.00"
                            },
                            {
                                "id": "9c677d71-a314-4070-84e9-fbb0008c5bc5",
                                "city": "Denver - Downtown",
                                "zipCode": "80202",
                                "dayOfTheWeek": [
                                    "mon",
                                    "tue",
                                    "wed",
                                    "thur",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "20.00"
                            },
                            {
                                "id": "5aad3c25-0618-4e82-8056-4f5892d5e5af",
                                "city": "Denver - Uptown/Capitol Hill/Speer",
                                "zipCode": "80203",
                                "dayOfTheWeek": [
                                    "mon",
                                    "tue",
                                    "wed",
                                    "thur",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "20.00"
                            },
                            {
                                "id": "8d5e3f61-4cd4-436b-896a-81aa833c6a1c",
                                "city": "Denver - Cherry Creek/East Colfax",
                                "zipCode": "80206",
                                "dayOfTheWeek": [
                                    "mon",
                                    "tue",
                                    "wed",
                                    "thur",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "20.00"
                            },
                            {
                                "id": "41ab765e-9c5f-4b58-a9b0-c87330566f9c",
                                "city": "Denver - Washington Park",
                                "zipCode": "80209",
                                "dayOfTheWeek": [
                                    "mon",
                                    "tue",
                                    "wed",
                                    "thur",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "20.00"
                            },
                            {
                                "id": "0f40c0bc-516e-4615-b9e6-fc04bc9679e7",
                                "city": "Denver - University/DU/Broadway",
                                "zipCode": "80210",
                                "dayOfTheWeek": [
                                    "mon",
                                    "tue",
                                    "wed",
                                    "thur",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "20.00"
                            },
                            {
                                "id": "2012724e-936e-49fd-9000-e8814e3381db",
                                "city": "Denver - City Park/Colfax",
                                "zipCode": "80218",
                                "dayOfTheWeek": [
                                    "mon",
                                    "tue",
                                    "wed",
                                    "thur",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "20.00"
                            },
                            {
                                "id": "4f540b71-05fa-47b8-8495-82095fa48ab3",
                                "city": "Denver-North Washington",
                                "zipCode": "80229",
                                "dayOfTheWeek": [
                                    "mon",
                                    "tue",
                                    "wed",
                                    "thur",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "20"
                            }
                        ],
                        "startTime": "08:00"
                    },
                    "created": "2019-12-19T16:48:29.280Z",
                    "lastUpdated": "2022-07-08T19:23:46.600Z",
                    "deleted": 0
                },
                "misc": {
                    "cancelled": true,
                    "backHaul": false,
                    "training": false,
                    "notes": "NO ROUTE"
                }
            }
        ],
        "2": [
            {
                "driver": {
                    "id": "3c0f8766-1e60-44c1-a563-fd62c41ebb45",
                    "name": "Hunter Brooks-1",
                    "phone": "(720) 636-6159",
                    "email": "etrnlove0@yahoo.com",
                    "lic": "06-181-1242",
                    "created": "2021-06-16T09:53:19.209Z",
                    "lastUpdated": "2024-05-10T15:17:07.389Z",
                    "occLic": "M90925"
                },
                "vehicle": {
                    "id": "894604ac-e79e-41f0-b643-4c624024ef1a",
                    "name": "Ford Transit",
                    "lic": "ABI-Q47",
                    "created": "2023-01-07T16:53:09.151Z",
                    "lastUpdated": "2024-07-15T23:30:15.598Z",
                    "data": false,
                    "vin": null,
                    "year": null,
                    "mileage": null,
                    "status": null
                },
                "route": {
                    "id": "6e23f85b-e74d-4ccb-a328-c0baff0032e5",
                    "name": "Pueblo County",
                    "data": {
                        "rows": [
                            {
                                "id": "1d5b3e84-4438-4653-a271-35a54549b0a7",
                                "city": "Pueblo",
                                "zipCode": "81001",
                                "dayOfTheWeek": [
                                    "tue",
                                    "thur"
                                ],
                                "biWeekly": false,
                                "price": "45.00"
                            },
                            {
                                "id": "52958448-57db-4b0a-ae6e-7eea969f1602",
                                "city": "Pueblo",
                                "zipCode": "81003",
                                "dayOfTheWeek": [
                                    "tue",
                                    "thur"
                                ],
                                "biWeekly": false,
                                "price": "45.00"
                            },
                            {
                                "id": "482ea0b5-2a6d-47ce-813c-f8b81c004bfe",
                                "city": "Pueblo",
                                "zipCode": "81004",
                                "dayOfTheWeek": [
                                    "tue",
                                    "thur"
                                ],
                                "biWeekly": false,
                                "price": "45.00"
                            },
                            {
                                "id": "6575aa79-f1ad-4131-a9b0-265798a6ea83",
                                "city": "Pueblo",
                                "zipCode": "81005",
                                "dayOfTheWeek": [
                                    "tue",
                                    "thur"
                                ],
                                "biWeekly": false,
                                "price": "45.00"
                            },
                            {
                                "id": "654681c4-bd93-4bee-9ef8-13679cfc5b44",
                                "city": "Pueblo",
                                "zipCode": "81006",
                                "dayOfTheWeek": [
                                    "tue",
                                    "thur"
                                ],
                                "biWeekly": false,
                                "price": "45.00"
                            },
                            {
                                "id": "893ce570-290b-4c6b-a66e-d82f5aed964c",
                                "city": "Pueblo",
                                "zipCode": "81007",
                                "dayOfTheWeek": [
                                    "tue",
                                    "thur"
                                ],
                                "biWeekly": false,
                                "price": "45.00"
                            },
                            {
                                "id": "c0ce78ae-d983-4a88-af09-f53f6183b582",
                                "city": "Pueblo",
                                "zipCode": "81008",
                                "dayOfTheWeek": [
                                    "tue",
                                    "thur"
                                ],
                                "biWeekly": false,
                                "price": "45.00"
                            },
                            {
                                "id": "5ffa7bff-437e-45b9-9726-6f551cf25fe3",
                                "city": "Canon City",
                                "zipCode": "81212",
                                "dayOfTheWeek": [
                                    "thur"
                                ],
                                "biWeekly": false,
                                "price": "50.00"
                            },
                            {
                                "id": "f4e1c37b-e902-444b-9d76-148411718339",
                                "city": "Penrose",
                                "zipCode": "81240",
                                "dayOfTheWeek": [
                                    "thur"
                                ],
                                "biWeekly": false,
                                "price": "40.00"
                            },
                            {
                                "id": "6d1e86ed-d178-490d-9265-8ba28ada8d37",
                                "city": "Florence",
                                "zipCode": "81290",
                                "dayOfTheWeek": [
                                    "thur"
                                ],
                                "biWeekly": false,
                                "price": "55.00"
                            },
                            {
                                "id": "0891ff14-38c4-48a8-be30-39b2d5b8de96",
                                "city": "Rockvale",
                                "zipCode": "81226",
                                "dayOfTheWeek": [
                                    "thur"
                                ],
                                "biWeekly": false,
                                "price": "55.00"
                            }
                        ],
                        "startTime": "06:00"
                    },
                    "created": "2019-12-18T22:24:13.835Z",
                    "lastUpdated": "2022-10-14T18:19:51.177Z",
                    "deleted": 0
                },
                "misc": {
                    "notes": "",
                    "training": false
                }
            }
        ],
        "3": [
            {
                "driver": {
                    "id": "3c0f8766-1e60-44c1-a563-fd62c41ebb45",
                    "name": "Hunter Brooks-1",
                    "phone": "(720) 636-6159",
                    "email": "etrnlove0@yahoo.com",
                    "lic": "06-181-1242",
                    "created": "2021-06-16T09:53:19.209Z",
                    "lastUpdated": "2024-05-10T15:17:07.389Z",
                    "occLic": "M90925"
                },
                "vehicle": {
                    "id": "8043f6f0-b5a6-429e-bbb9-37aa6b40f690",
                    "name": "Ram Promaster",
                    "lic": "AIK-T08",
                    "created": "2022-10-28T02:54:53.812Z",
                    "lastUpdated": "2024-07-15T23:30:16.417Z",
                    "data": {},
                    "vin": null,
                    "year": null,
                    "mileage": null,
                    "status": null
                },
                "route": {
                    "id": "ccf20d0a-ee26-40df-8a2b-9286da832ec9",
                    "name": "Northern Colorado",
                    "data": {
                        "rows": [
                            {
                                "id": "bc56f8e7-1f0c-4733-9a4f-a589c388a0e5",
                                "city": "Fort Collins",
                                "zipCode": "80521",
                                "dayOfTheWeek": [
                                    "wed",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "35.00"
                            },
                            {
                                "id": "0e04e0e9-94b7-4159-b62f-6bed0ccd617a",
                                "city": "Fort Collins",
                                "zipCode": "80524",
                                "dayOfTheWeek": [
                                    "wed",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "35.00"
                            },
                            {
                                "id": "252d65a9-c301-4f4f-bb79-abe17ca1557a",
                                "city": "Fort Collins",
                                "zipCode": "80525",
                                "dayOfTheWeek": [
                                    "wed",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "35.00"
                            },
                            {
                                "id": "2c3090db-c5f7-46bd-b37a-a6bce1c2b438",
                                "city": "Fort Collins",
                                "zipCode": "80526",
                                "dayOfTheWeek": [
                                    "wed",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "35.00"
                            },
                            {
                                "id": "4dd38db6-90b3-493d-893d-e81d1f53358f",
                                "city": "Fort Collins",
                                "zipCode": "80528",
                                "dayOfTheWeek": [
                                    "wed",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "35.00"
                            },
                            {
                                "id": "ef425741-a55d-4108-97cb-78337657cfc7",
                                "city": "Garden City",
                                "zipCode": "80631",
                                "dayOfTheWeek": [
                                    "wed",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "40.00"
                            },
                            {
                                "id": "c3d197b7-8057-44e1-b7da-043f6f385297",
                                "city": "Berthoud",
                                "zipCode": "80513",
                                "dayOfTheWeek": [
                                    "wed",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "30.00"
                            },
                            {
                                "id": "3d2a3b8e-8bc0-4120-bd81-85da3b8a7afc",
                                "city": "Windsor",
                                "zipCode": "80528",
                                "dayOfTheWeek": [
                                    "wed",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "40.00"
                            },
                            {
                                "id": "299ff46b-f0fd-42a0-b78d-a6a97b0d2237",
                                "city": "Windsor",
                                "zipCode": "80550",
                                "dayOfTheWeek": [
                                    "wed",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "40.00"
                            },
                            {
                                "id": "63313e86-f4d1-469c-9aaa-a1a3433e7c1b",
                                "city": "Milliken",
                                "zipCode": "80543",
                                "dayOfTheWeek": [
                                    "wed",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "40.00"
                            },
                            {
                                "id": "1a61eb47-16a6-430c-baae-9d71537ba88a",
                                "city": "Thornton/Henderson",
                                "zipCode": "80602",
                                "dayOfTheWeek": [
                                    "wed",
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "25.00"
                            },
                            {
                                "id": "d3c4680d-6dd2-4cd3-8ab4-5437eeb7f396",
                                "city": "Sedgwick",
                                "zipCode": "80749",
                                "dayOfTheWeek": [
                                    103,
                                    117
                                ],
                                "biWeekly": false,
                                "price": "60.00"
                            },
                            {
                                "id": "f5e99fcc-d89e-4da3-9e95-29ec7f59efb1",
                                "city": "Log Lane Village",
                                "zipCode": "80705",
                                "dayOfTheWeek": [
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "50.00"
                            },
                            {
                                "id": "2244fa5a-43ff-4440-8c52-f33eb473e926",
                                "city": "Wellington",
                                "zipCode": "80549",
                                "dayOfTheWeek": [
                                    "fri"
                                ],
                                "biWeekly": false,
                                "price": "55.00"
                            }
                        ],
                        "startTime": "07:00"
                    },
                    "created": "2019-12-18T22:24:13.809Z",
                    "lastUpdated": "2025-02-11T17:33:27.078Z",
                    "deleted": 0
                },
                "misc": {
                    "training": false,
                    "notes": "",
                    "backHaul": false
                }
            }
        ],
        "5": [
            {
                "driver": {
                    "id": "7b4347ac-d11d-4d34-9480-92b3fc139d21",
                    "name": "Joel Dickerson",
                    "phone": "(620) 757-6087",
                    "email": "joel@greenparcelservice.com",
                    "lic": "15-253-0364",
                    "created": "2021-09-20T13:28:43.411Z",
                    "lastUpdated": "2024-05-10T15:17:07.259Z",
                    "occLic": "M49527"
                },
                "misc": {}
            }
        ],
        "6": [
            {
                "driver": {
                    "id": "7b4347ac-d11d-4d34-9480-92b3fc139d21",
                    "name": "Joel Dickerson",
                    "phone": "(620) 757-6087",
                    "email": "joel@greenparcelservice.com",
                    "lic": "15-253-0364",
                    "created": "2021-09-20T13:28:43.411Z",
                    "lastUpdated": "2024-05-10T15:17:07.259Z",
                    "occLic": "M49527"
                },
                "misc": {}
            }
        ],
        "7": [
            {
                "driver": {
                    "id": "7b4347ac-d11d-4d34-9480-92b3fc139d21",
                    "name": "Joel Dickerson",
                    "phone": "(620) 757-6087",
                    "email": "joel@greenparcelservice.com",
                    "lic": "15-253-0364",
                    "created": "2021-09-20T13:28:43.411Z",
                    "lastUpdated": "2024-05-10T15:17:07.259Z",
                    "occLic": "M49527"
                },
                "misc": {}
            }
        ]
    }
}
```
