# 0x01. ES6 Promises

## Overview
This project focuses on ES6 Promises in JavaScript. It covers the fundamental concepts of promises, how to use them, and their role in handling asynchronous operations in JavaScript.

## Learning Objectives
By the end of this project, you should be able to:
- Explain what promises are and why they are used.
- Use `then`, `resolve`, and `catch` methods of promises.
- Utilize every method of the Promise object.
- Implement `try/catch` blocks.
- Understand and use the `await` operator and `async` functions.

## Requirements
- All code files will be executed on Ubuntu 18.04 LTS using NodeJS 12.11.x.
- Use allowed editors: vi, vim, emacs, Visual Studio Code.
- All files should end with a new line.
- A `README.md` file at the root of the project directory is mandatory.
- Code should use the `.js` extension.
- Code will be tested using Jest (`npm run test`).
- Code will be verified against lint using ESLint.
- All functions must be exported.

## Setup
1. **Install NodeJS 12.11.x**:
    ```sh
    curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh
    sudo bash nodesource_setup.sh
    sudo apt install nodejs -y
    nodejs -v
    # Output: v12.11.1
    npm -v
    # Output: 6.11.3
    ```

2. **Install Jest, Babel, and ESLint**:
    In your project directory, install Jest, Babel, and ESLint using the supplied `package.json` file:
    ```sh
    npm install
    ```

## Configuration Files
Add the following configuration files to your project directory:

- `package.json`
- `babel.config.js`
- `utils.js`
- `.eslintrc.js`

## Response Data Format
- `uploadPhoto` returns:
    ```json
    {
      "status": 200,
      "body": "photo-profile-1"
    }
    ```
- `createUser` returns:
    ```json
    {
      "firstName": "Guillaume",
      "lastName": "Salva"
    }
    ```

## Tasks

### Task 0: Keep every promise you make and only make promises you can keep
File: `0-promise.js`

Write a function `getResponseFromAPI` that returns a promise.

```js
export default function getResponseFromAPI() {
    return new Promise((resolve) => {
        resolve();
    });
}
```

### Task 1: Don't make a promise...if you know you can't keep it
File: `1-promise.js`

Write a function `getFullResponseFromAPI` that accepts a boolean parameter and returns a promise.

```js
export default function getFullResponseFromAPI(success) {
    return new Promise((resolve, reject) => {
        if (success) {
            resolve({ status: 200, body: 'Success' });
        } else {
            reject(new Error('The fake API is not working currently'));
        }
    });
}
```

### Task 2: Catch me if you can!
File: `2-then.js`

Write a function `handleResponseFromAPI` that appends handlers to a promise.

```js
export default function handleResponseFromAPI(promise) {
    return promise
        .then(() => ({ status: 200, body: 'success' }))
        .catch(() => new Error())
        .finally(() => console.log('Got a response from the API'));
}
```

### Task 3: Handle multiple successful promises
File: `3-all.js`

Write a function `handleProfileSignup` that imports and uses `uploadPhoto` and `createUser` from `utils.js`.

```js
import { uploadPhoto, createUser } from './utils';

export default function handleProfileSignup() {
    return Promise.all([uploadPhoto(), createUser()])
        .then((responses) => {
            console.log(`${responses[0].body} ${responses[1].firstName} ${responses[1].lastName}`);
        })
        .catch(() => {
            console.log('Signup system offline');
        });
}
```

### Task 4: Simple promise
File: `4-user-promise.js`

Write a function `signUpUser` that returns a resolved promise with the user object.

```js
export default function signUpUser(firstName, lastName) {
    return Promise.resolve({ firstName, lastName });
}
```

### Task 5: Reject the promises
File: `5-photo-reject.js`

Write a function `uploadPhoto` that returns a rejected promise with an error.

```js
export default function uploadPhoto(filename) {
    return Promise.reject(new Error(`${filename} cannot be processed`));
}
```

### Task 6: Handle multiple promises
File: `6-final-user.js`

Write a function `handleProfileSignup` that calls `signUpUser` and `uploadPhoto`, and handles their promises.

```js
import signUpUser from './4-user-promise';
import uploadPhoto from './5-photo-reject';

export default function handleProfileSignup(firstName, lastName, fileName) {
    return Promise.allSettled([signUpUser(firstName, lastName), uploadPhoto(fileName)])
        .then((results) => {
            return results.map((result) => ({
                status: result.status,
                value: result.value || result.reason,
            }));
        });
}
```

### Task 7: Load balancer
File: `7-load_balancer.js`

Write a function `loadBalancer` that returns the value of the first resolved promise.

```js
export default function loadBalancer(chinaDownload, USDownload) {
    return Promise.race([chinaDownload, USDownload]);
}
```

### Task 8: Throw error / try catch
File: `8-try.js`

Write a function `divideFunction` that throws an error if the denominator is 0.

```js
export default function divideFunction(numerator, denominator) {
    if (denominator === 0) {
        throw new Error('cannot divide by 0');
    }
    return numerator / denominator;
}
```

### Task 9: Throw an error
File: `9-try.js`

Write a function `guardrail` that handles errors and appends results to a queue.

```js
export default function guardrail(mathFunction) {
    const queue = [];
    try {
        const result = mathFunction();
        queue.push(result);
    } catch (error) {
        queue.push(error.toString());
    } finally {
        queue.push('Guardrail was processed');
    }
    return queue;
}
```

### Task 10: Await / Async
File: `100-await.js`

Write an async function `asyncUploadUser` that calls `uploadPhoto` and `createUser`.

```js
import { uploadPhoto, createUser } from './utils';

export default async function asyncUploadUser() {
    try {
        const [photo, user] = await Promise.all([uploadPhoto(), createUser()]);
        return { photo, user };
    } catch (error) {
        return { photo: null, user: null };
    }
}
```

## Running the Project
To run the project and test the implemented functions, use the following commands:

```sh
# To install dependencies
npm install

# To run tests
npm run test

# To run a specific file (e.g., 0-main.js)
npm run dev 0-main.js
```

## Conclusion
This project enhances your understanding of ES6 Promises and how they can be used to handle asynchronous operations effectively in JavaScript. It covers basic promise creation, chaining, error handling, and combining multiple promises using various methods.
