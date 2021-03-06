# ax-request-builder

*2.0.0-unstable*

npm module that helps you to send build config and send requests using axios throw async methods 

## install
```shell
npm install ax-request-builder --save
```

## uninstall
```shell
npm uninstall ax-request-builder --save
```

## Usage
```js
/*
* Import class to the project
*/
const { Ax } = require('ax-request-builder');

/*
* Create an object of rhe class Ax. As an argument put there the base url to server you are going to send requests to.
*/
const ax = new Ax('http://localhost:8080');

// Here we set the parameter for switch case.
const method = 'GET';

/*
* Using of methods must be in async function.
*/
(async () => {
    switch (method){
        //  Usage of method get
        case "GET":
            /*
            * All methods return fields status (response http status) and data (server response object)
            */
            var { status, data } = await ax.GET(
                '/api/v1/users', // route - a part of url without base part, that you've set, when was creating the object of class.
                'Jack228', // param - you can set one param in url with this module.
                { name: "Jack", age: 17 } // query - your query params in object
            )
            console.log({ status, data }); // Log module response to console.
            break;
        //  Usage of method post
        case "POST":
            var { status, data } = await ax.POST(
                '/api/v1/users',
                'Jack228',
                { name: "Jack", age: 27 },
                {   // body parameters in object.
                    lastname: "Jackson",
                    city: "Westminster",
                    job: "junior nodejs"
                }
            )
            console.log({ status, data });
            break;
        //  Usage of method patch
        case "PATCH":
            var { status, data } = await ax.PATCH(
                '/api/v1/users',
                'Jack228',
                { name: "Jack", age: 28 },
                {
                    lastname: "Jackson",
                    city: "Westminster",
                    job: "middle nodejs"
                }
            )
            console.log({ status, data });
            break;
        //  Usage of method delete
        case "DELETE":
            var { status, data } = await ax.PATCH(
                '/api/v1/users',
                'Jack228',
                { name: "Jack", age: 28 },
                {
                    lastname: "Jackson",
                    city: "Westminster",
                    job: "middle nodejs"
                }
            )
            console.log({ status, data });
            break;
        default:
            console.log('DEFAULT');
    }
})()
```

## References
* support: glabstrizhkovgit@gmail.com
* github: https://github.com/glabStrizhkov/ax-request-builder