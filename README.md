# node-test-app

A quick Node.js test using [Express 4](http://expressjs.com/).

## Running Locally

Make sure you have [Node.js](http://nodejs.org/)

```sh
git clone git@github.com:wibidev/node-test-app.git # or clone your own fork
cd node-test-app
npm install
npm start
```

## Instructions

This small RESTful API will make requests to an external web service: https://shibe.online/.
You have to build several endpoints that returns JSON.
Feel free to organize your files like it is a real API (think scalability).

### GET /animals/shibes
Will make a synchronous request to fetch shibes from the external API.

### GET /animals/cats
Will make a synchronous request to fetch cats from the external API.

### GET /animals/birds
Will make a synchronous request to fetch birds from the external API.

### GET /animals/all
Will make asynchronous requests to fetch cats birds & shibes.

| Querystring parameter     |     Description       |     Required      | Default value  | Validations |
| ------------- |------------- |-------------| -----| -----|
| protocol  | Get https or http urls     | yes | none |Can only accept http or https |
| count   | Number of entries per animal type to return    | no      | 1  | Must be a number, min 1, max 30 |
| url | Get full URL or image ID   |   no      | true  |  true/false|

### Possible JSON outputs:

#### Success
```javascript
{
  type: 'success',
  code: 200,
  total: 1,
  data: {
    // GET /animals/shibes
    shibes: [
      { 
        // if url = false
        id: '404ae6ed024aa5f1b9001fd755abdebe87886a0e',
        // if url = true
        url: 'http://cdn.shibe.online/shibes/404ae6ed024aa5f1b9001fd755abdebe87886a0e.jpg' 
      }
    ],
    // GET /animals/shibes
    cats: [
      { 
        // if url = false
        id: '404ae6ed024aa5f1b9001fd755abdebe87886a0e',
        // if url = true
        url: 'http://cdn.shibe.online/shibes/404ae6ed024aa5f1b9001fd755abdebe87886a0e.jpg' 
      }
    ],
    // GET /animals/shibes
    birds: [
      { 
        // if url = false
        id: '404ae6ed024aa5f1b9001fd755abdebe87886a0e',
        // if url = true
        url: 'http://cdn.shibe.online/shibes/404ae6ed024aa5f1b9001fd755abdebe87886a0e.jpg' 
      }
    ],
    // GET /animals/all
    animals: [
      { 
        type: 'shibe', 
        // if url = false
        id: '404ae6ed024aa5f1b9001fd755abdebe87886a0e', 
        // if url = true
        url: 'http://cdn.shibe.online/shibes/404ae6ed024aa5f1b9001fd755abdebe87886a0e.jpg' 
      }
    ]
  }
}

```

#### Bad request

```
{
  type: 'badRequest',
  code: 400,
  errors: [
    { 
      param: 'protocol',
      message: ERROR_MESSAGE
    },
    { 
      param: 'count',
      message: ERROR_MESSAGE
    },
    { 
      param: 'url',
      message: ERROR_MESSAGE
    }
  ]
}

```

### Bonus:

Make a middleware that catch and log errors
