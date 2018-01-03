# Frost client

The Frost client is an npm package. This package exposes the methods for communicating with the API Frost.


---
## Guide

- [How to install](#how-to-install)
- [Import Frost](#import-frost)
- [Methods](#methods)
    - [Initialization](#initialization)
    - [create](#create)
    - [login](#login)
    - [verifyAccount](#verify-account)
    - [forgotPassword](#forgot-password)
    - [changePassword](#change-password)
    - [createWork](#create-work)
    - [getWork](#get-work)
    - [getWorks](#get-works)

---


## How to install

```bash
$ npm install @poetapp/frost-client
```

```bash
$ yarn add @poetapp/frost-client
```

```bash
$ git clone git@github.com:poetapp/frost-client.git
$ cd frost-client && npm link
```

## Import Frost

```javascript
import { Frost } from '@poetapp/frost-client'
```

```javascript
const { Frost } = require('@poetapp/frost-client')
```


## Methods


## Initialization

```javascript

import { Frost } from '@poetapp/frost-client'

const config = {
    host: 'api.frost.po.et', // required
    email: 'email@cool.com',
    password: 'xxxxxxx'
}

const frost = new Frost(config)

```

## Create

With this method, you will be able to create a new account in Frost. The method create is a promise, it will return an object but if occur an error it will throw an error message.


Example with async/await

```javascript

const createFrostAccount = async() => {
    try {

        // if you set email and password in your config, you only need to do this.
        const { token } = await frost.create()
        
        /* if not...
        
        const { token } = await frost.create('email@cool.com', 'xxxxxxx')

        */

    } catch(e) {
        console.log(e)
    }

}

createFrostAccount()

```

## Login

With this method, you will be able to login to your Frost account. The method login is a promise, it will return an object but if occur an error it will throw an error message.

Example with async/await

```javascript

const loginFrostAccount = async() => {
    try {

        // if you set email and password in your config, you only need to do this.
        const { token } = await frost.login()
        
        /* if not...
        
        const { token } = await frost.login('email@cool.com', 'xxxxxxx')

        */

    } catch(e) {
        console.log(e)
    }

}

loginFrostAccount()

```

## Verify account

With this method, Frost will send the email to verify your email account. This action is required to create works.

Example with async/await

```javascript

const verifyFrostAccount = async() => {
    try {

       await frost.verifyAccount(token)

    } catch(e) {
        console.log(e)
    }

}

verifyFrostAccount()

```


## Forgot password

With this method, you will be able to change your password. Frost will send an email with a new token for you use the method ** frost.changePassword **. The method forgotPassword is a promise if occur an error it will throw an error message.

Example with async/await

```javascript

const forgotFrostPassword = async() => {
    try {

        // if you set email and password in your config, you only need to do this.
        await frost.forgotPassword()
        
        /* if not...
        
        await frost.forgotPassword('email@cool.com')

        */

    } catch(e) {
        console.log(e)
    }

}

forgotFrostPassword()

```


## Change password

With this method, you will be able to change your password. This method requires a token and your account verified. The method changePassword is a promise if occur an error it will throw an error message.

Example with async/await

```javascript

const changeFrostPassword = async() => {
    try {

        const newPassword = 'xxxxxxx'
        await frost.changePassword(token, newPassword)

    } catch(e) {
        console.log(e)
    }

}

changeFrostPassword()

```

## Create work

With this method, you will be able to create a work. The method createWork is a promise, it will return an object but if occur an error it will throw an error message.


Example with async/await

```javascript

const createWork = async() => {
    try {

        const work = {
            name: 'My first work in Frost',
            datePublished: '2017-11-24T00:38:41.595Z', // ISO date
            dateCreated: '2017-11-24T00:38:41.595Z', // ISO date
            author: 'Me'
            tags: 'Frost,the best', // tags separation by commas
            content: 'The best content'
        }

        const { workId } = await frost.createWork(token, work)

    } catch(e) {
        console.log(e)
    }

}

createWork()

```

## Get work

With this method, you will be able to get a work. The method getWork is a promise, it will return an object but if occur an error it will throw an error message.

Example with async/await

```javascript

const getWork = async() => {
    try {

        const workId = '123456'
        const work = await frost.getWork(token, workId)

    } catch(e) {
        console.log(e)
    }

}

getWork()

```

## Get works

With this method, you will be able to get all your works. The method getWorks is a promise, it will return an object but if occur an error it will throw an error message.

Example with async/await

```javascript

const getAllWorks = async() => {
    try {

        const works = await frost.getWorks(token)

    } catch(e) {
        console.log(e)
    }

}

getAllWorks()

```
