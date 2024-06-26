
# GO-ing Serverless: A Gin fuel Journey into microservices!! 

## Usefull Links.
### Demos Available
1. PetStore API - [Link](https://github.com/deepmap/oapi-codegen/tree/master/examples/petstore-expanded/gin) to documentation for a pet store API
2. go-Swagger PetStore Example [Link](https://github.com/go-swagger/go-swagger/tree/master/examples/2.0/petstore/server)
3.Book Store Example - [Link](https://pkg.go.dev/github.com/hairizuanbinnoorazman/golang-web-gin-book-store#section-readme)
4. GIN & React web app - [Link](https://github.com/southwolf/gin-react-demo?tab=readme-ov-file)
5. React PetStore FrontEnd [Link](https://github.com/chubbyts/react-petstore/tree/master/src)
6. Petstore [link](https://github.com/deepmap/oapi-codegen/tree/master/examples/petstore-expanded/gin/api)
7. Petstore gin [link](https://github.com/OpenAPITools/openapi-generator/blob/master/samples/server/petstore/go-gin-api-server/go/README.md)

# Introduction
This project is born from a AWS MeetUp Group talk about Go and Serverless microservice architecture. I used this as an example [link](goes-here), so thank you to @yannhe. 

# Technology
1. Docker
2. GoLang
3. AWS Lambda
4. API Gateway
5. AWS SAM

# Concepts
To demostrate how one to used GO and lambda to create a serverless architecture from a monolith service i broke down the initial repo into the 4 lambda functions (GET,DELETE,POST,PUT). Although not a real world scnerio it clearly demonstrates how you can take a project and separate into microservices so the restAPI methods were used ad the sorting method but in a real project this would be something like user registration , fetch data from database , etc ...

# How to deploy
## Build
sam build
# Testing
sam local start-api -p 8080
# Deploy
sam deploy --guided



# Pet Store Original README

To whom it may concern,
This app will allow you to store and retrieve pets.

I believe there are a few issues in the code but it is doing 99% of what it is supposed to do.
If you see a bug, please open an issue.

## Build status

[![CircleCI](https://circleci.com/gh/YannHulot/petstore/tree/master.svg?style=svg)](https://circleci.com/gh/YannHulot/petstore/tree/master)

## Motivation

This project is demonstration of my skills in different areas such as API design and Golang development work.

## Code style

Code is formatted with Go vet and Go fmt.

The linter golangci-lint is used to ensure the highest code quality and avoid potential bugs.

## Tech/framework used

Written in Golang, this project uses may open source libraries and frameworks such as for example:

- Gin router
- Gorm database ORM
- SQLMock to mock database interactions
- PostgreSQL as a database
- Docker for easy deployment

## Examples of queries

### Save a Pet

### Example of payload when saving a new pet

```json
{
    "category": {
        "id": 90,
        "name": "test-category"
    },
    "name": "pet 87",
    "photoUrls": [
        "testurl",
        "t39"
    ],
    "tags": [
    {
        "id": 8990,
        "name": "test-category 2"
    },{
        "id": 79,
        "name": "test-category 2"
    }],
    "status": "sold"
}
```

### Save a pet

```curl
curl -v -XPOST -H "Content-type: application/json" -d '{
    "category": {
        "id": 90,
        "name": "test-category"
    },
    "name": "pet 87",
    "photoUrls": [
        "testurl",
        "t39"
    ],
    "tags": [
    {
        "id": 8990,
        "name": "test-category 2"
    },{
        "id": 79,
        "name": "test-category 2"
    }],
    "status": "sold"
}' 'http://localhost:8080/api/v1/pet'
```

Or use your favorite request tool creator such as Postman.

### Get a pet

```curl
curl -XGET 'http://localhost:8080/api/v1/pet/1'
```

### Delete a pet

```curl
curl -XDELETE 'http://localhost:8080/api/v1/pet/1'
```

### Get pets by status

```curl
curl -XGET 'http://localhost:8080/api/v1/pet/findByStatus?status=sold'
```

#### Get pet with multiple statuses

```curl
curl -XGET 'http://localhost:8080/api/v1/pet/findByStatus?status=sold&status=pending'
```

### Update a pet's attributes via form data

```curl
curl -X POST "http://localhost:8080/api/v1/pet/8" -H  "accept: application/json" -H  "Content-Type: application/x-www-form-urlencoded" -d "name=doggyboy&status=taken"
```

### Update a pet's image

```curl
curl -X POST "http://localhost:8080/api/v1/pet/1/uploadImage" -H  "accept: application/json" -H  "Content-Type: multipart/form-data" -F "additionalMetadata=test" -F "file=@name-of-your-file.png;type=image/png"
```

## Error responses

Errors will be returned in this format:

```json
{
  "type": "error",
  "message" : "this is an error"
}
```

## Installation

Steps:

```bash
git clone https://github.com/YannHulot/petstore
```

```bash
cd petstore
```

```bash
docker-compose up --build
```

Wait about 2 minutes for everything to be set up depending on your internet speed and for the different services to start.

If everything went well you should now have the server running on port 8080

## Shut down the application

```bash
docker-compose down
```

### Warning

I would suggest to not change the env variables unless you know what you are doing.

## API Reference

The API reference can be found at: <https://petstore.swagger.io/>

## Tests

The tests can be run by using the command: `go test ./...`

## Credits

I Found help on Stack Overflow, Medium and in other parts of the internet.

## License

MIT License

Copyright (c)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.