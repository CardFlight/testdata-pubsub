# Test Data for PubSub

This repository houses data that can be used to exercise Pub/Sub integrations.  The intention is
to use [My JSON Server](https://my-json-server.typicode.com/) as a server of the notification
payload.

## A High-Level Overview of Pub/Sub

1.  The client sends a `POST` message to `<server>/vantiv/notifications`
2.  The server schedules a job to retrieve the notification payload
3.  The server retrieves the payload from a know URL & uses that to open, close, or modify accounts

In our test environments, the server will accept an additional parameter in the `POST` body to
specify where to retrieve the notification payload.  We can use that with some additional tools
to perform integration testing on the Pub/Sub integration.

## To Use
1.  Make this repo public
2.  Validate you can see the data from `db.json` here:  

```
https://my-json-server.typicode.com/CardFlight/testdata-pubsub/db
```

3.  Modify `db.json` to contain the notifications you want it to.

3.  POST to our testing server to start the process.  See `notification.json` for a sample of how to
format it.

4.  Verify the interactions worked as expected in Overwatch.

5.  Make this repo private again.

## To Make It Better

We could run our own instance of [json-server](https://github.com/typicode/json-server) within our
own infrastructure.  This would allow us to keep this repository private, and give a lot more
flexibility to our testing.
