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
    "Access-Token": "5c23b2cf-6b02-411c-b3b2-6c223422fc6g", //the access token provided to the vendor by GPS. This is unique and should not be shared
  },
  body: JSON.stringify({
    "date": "2025-03-16T00:00:00.000Z" //this is a UTC date referencing the start of the week, ie sunday.
  }),
};
```