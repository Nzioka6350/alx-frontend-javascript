To get started with your project on ES6 classes, OOP, and JavaScript, you'll need to follow these steps. I'll guide you through each of the requirements, including the setup and configuration files.

### Step 1: Setting up NodeJS 12.11.x

1. **Install NodeJS 12.11.x**:
   Open your terminal and run the following commands:

   ```bash
   curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh
   sudo bash nodesource_setup.sh
   sudo apt install nodejs -y
   ```

2. **Verify the installation**:
   Check the installed versions to ensure they match the required versions:

   ```bash
   nodejs -v
   # Should output: v12.11.1

   npm -v
   # Should output: 6.11.3
   ```

### Step 2: Install Jest, Babel, and ESLint

1. **Create your project directory** (if you haven't already):

   ```bash
   mkdir es6-classes-project
   cd es6-classes-project
   ```

2. **Add configuration files**:
   Create the following files in your project directory:

   **package.json**:
   ```json
   {
     "name": "es6-classes-project",
     "version": "1.0.0",
     "description": "Project for learning ES6 classes and OOP in JavaScript",
     "main": "index.js",
     "scripts": {
       "test": "jest",
       "lint": "eslint .",
       "full-test": "npm run lint && npm run test"
     },
     "author": "Your Name",
     "license": "ISC",
     "dependencies": {
       "@babel/core": "^7.8.7",
       "@babel/preset-env": "^7.8.7"
     },
     "devDependencies": {
       "jest": "^24.9.0",
       "eslint": "^6.8.0",
       "babel-jest": "^24.9.0"
     }
   }
   ```

   **babel.config.js**:
   ```javascript
   module.exports = {
     presets: [['@babel/preset-env', { targets: { node: 'current' } }]],
   };
   ```

   **.eslintrc.js**:
   ```javascript
   module.exports = {
     env: {
       es6: true,
       node: true,
       jest: true,
     },
     extends: 'eslint:recommended',
     globals: {
       Atomics: 'readonly',
       SharedArrayBuffer: 'readonly',
     },
     parserOptions: {
       ecmaVersion: 2018,
       sourceType: 'module',
     },
     rules: {
       'no-console': 'off',
     },
   };
   ```

3. **Install the dependencies**:
   Run the following command to install Jest, Babel, and ESLint:

   ```bash
   npm install
   ```

### Step 3: Create a README.md file

Create a `README.md` file in the root of your project directory with the following content:

```markdown
# ES6 Classes Project

## Description

This project is designed to help you learn and practice ES6 classes and Object-Oriented Programming (OOP) concepts in JavaScript. 

## Learning Objectives

By the end of this project, you should be able to:

- Define a class in JavaScript.
- Add methods to a class.
- Understand why and how to add static methods to a class.
- Extend a class from another class.
- Understand metaprogramming and symbols.

## Setup

To set up the project, follow these steps:

1. Install NodeJS 12.11.x:
   ```bash
   curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh
   sudo bash nodesource_setup.sh
   sudo apt install nodejs -y
   ```

2. Verify the installation:
   ```bash
   nodejs -v
   # Should output: v12.11.1

   npm -v
   # Should output: 6.11.3
   ```

3. Install project dependencies:
   ```bash
   npm install
   ```

## Running Tests

To run the tests, use the following command:
```bash
npm run test
```

To run ESLint for code linting, use:
```bash
npm run lint
```

To run both linting and tests, use:
```bash
npm run full-test
```

## Author

James Mutua

```

### Step 4: Writing Your Classes and Tests

Now, you can start writing your JavaScript classes in files with the `.js` extension. Make sure to write test cases using Jest and place them in a `__tests__` directory or with a `.test.js` suffix.

### Example Class and Test

**classExample.js**:
```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    return `Hello, my name is ${this.name} and I am ${this.age} years old.`;
  }

  static species() {
    return 'Homo sapiens';
  }
}

module.exports = Person;
```

**__tests__/classExample.test.js**:
```javascript
const Person = require('../classExample');

test('Person class works correctly', () => {
  const person = new Person('John', 30);
  expect(person.greet()).toBe('Hello, my name is John and I am 30 years old.');
  expect(Person.species()).toBe('Homo sapiens');
});
```

### Conclusion

By following these steps, you'll be able to set up your environment and start working on the project requirements. Make sure your code passes all the tests and linting checks by running `npm run full-test`. Good luck!
