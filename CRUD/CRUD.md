# CRUD

CRUD is an acronym often used when thinking about a REST API.
It stands for

- Create
- Read or Retrieve
- Update
- Destroy or Delete

and is a reminder of the sorts of things you most likely want to be able to do with some data.

You might hear someone call a server built to handle data in this way a "CRUD Server" or a "CRUD Service".

## REST equivalents

REST API's have a number of methods that get sent with the request, but the most common ones used with a "CRUD server" are POST, GET, PUT and DELETE. With

- POST being the equivalent of Create
- GET being the equivalent of Read
- PUT being the equivalent of Update
- DELETE being the equivalent of Destroy

Express allows you to set handler functions for a particular url and method. For example a POST request to the url `\products`, to add a new product to a catalogue. We will not talk about the details of how you do this here, but will be included [here](./methodsInExpress.md).

## Sending and Receiving data

Data can be passed into your REST API app in two ways.

### Path and Query Parameters

Path and Query parameters are typically used to help identify a particular resource, for example it could be something like a product id or a user name. They aren't typically used to create or modify resource data directly.

You can add path parameters to any method in Express. We will not go into how you do this in this text but details can be found [here](./GetWithParams.md).

### Body Data

Body data is the data that is being transferred with the request. If it was a plain old HTTP request for a website then the body data would be the html text for the webpage that is specified by the url. However you can send more than just html via a http request. You might already know you can send pngs, pdfs, mp3 and mp4 data as well as many other types of data, but as well as receiving this data in response to a http request, you can also send it.

While you can send data in any format you like, typically you will see a data type called JSON.

JSON is an acronym for JavaScript Object Notation and is often used to send data around REST API apps. Again I won't go into details here, but you will see how to use JSON in an express app later. For now though I will leave you with this [link](https://en.wikipedia.org/wiki/JSON#Syntax) explaining the syntax of JSON data.

## Topics

- [Writing Methods in Express](./methodsInExpress.md)
- [Path And Query Parameters](./PathAndQueryParameters.md)
- [Using a router in Express](./router.md)
- [Using JSON Body Data](./Body.md)
- [Validating Inputs](./validation.md)
- [Example app](./example.md)