# What is API?

API stands for Application Programming Interface. It is a defined set of rules to define the methods of communication between different software components with each other.


# What is API Testing?
API testing involves testing the collection of APIs and to check if they meet expectations for:
i. functionality: Checks the response on basis of input (request) parameter
ii. reliability: Checks the response can be trusted and authenticated
iii. performance: Checks how much time the API is taking to retrieve 
iv. security: Checks if recieved response is authorised and secure data

It also involves determining whether the output is well-structured and useful to another application or not:
i. Checks the response on basis of input (request) parameter, (functionality)
ii. Checks how much time the API is taking to retrieve and authorise the data too (performance)


[link](https://medium.com/aubergine-solutions/api-testing-using-postman-323670c89f6d)


# Postman for API Testing
Postman is an application for testing APIs, by sending request to the web server and getting the response back. It has a interactive user interface and allows users to set up all the headers and cookies the API expects, and checks the response. Its useful for API Testing and Postman Behaviour Driven Development(BDD).

### Some relateable keywords to understand Postman:
* Request URL — It is where to make the http request
* Call methods: The most used request methods: GET, POST, PUT, DELETE
* Request Headers — In request headers it contains key-value of the application. This key-value could be : (i) Content-Type and (ii) Authorization.
* Tokenized authorization: An authorization token, included with requests, is used to identify the requester.
* Header: Define content type and content data
* Content-type: A content-type describes the format of object data. Content-type, which I have used the most for the requests and responses is application/json.
* Body: This contains the information to pass in various formats, like Json, Binary, raw, etc.
* API call: Triggered by simply clicking Send button.
* Test: A test in Postman is fundamentally a JavaScript code, which run after a request is sent and a response has been received from the server.
* HTTP Response: On sending request, API sends the response which consists of the Body, Cookies, Headers, Tests, Status code, and API Response Time.
* Response Code: 200 Success, 404 NOt Found, etc.

### Postman features makes it effective tool for testing increases the productivity:






Eg picture:
![filezilla1](/assets/networksecurity/filezilla1.png){:height="75%" width="75%"}

