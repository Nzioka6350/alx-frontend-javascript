# ES6 Basics

## Table of Contents
- [Project Overview](#project-overview)
- [Learning Objectives](#learning-objectives)
- [Requirements](#requirements)
- [Setup](#setup)
  - [Install NodeJS](#install-nodejs)
  - [Install Project Dependencies](#install-project-dependencies)
- [Configuration Files](#configuration-files)
  - [package.json](#packagejson)
  - [babel.config.js](#babelconfigjs)
  - [.eslintrc.js](#eslintrcjs)
- [Usage](#usage)
- [Resources](#resources)

## Project Overview

This project focuses on the basics of ECMAScript 6 (ES6), also known as ECMAScript 2015. You will learn about various new features introduced in ES6, such as arrow functions, default parameters, rest parameters, iterables, and more.

## Learning Objectives

By the end of this project, you should be able to explain:

- What ES6 is
- New features introduced in ES6
- The difference between a constant and a variable
- Block-scoped variables
- Arrow functions and function parameters default to them
- Rest and spread function parameters
- String templating in ES6
- Object creation and their properties in ES6
- Iterators and for-of loops

## Requirements

- All files will be executed on Ubuntu 18.04 LTS using NodeJS 12.11.x
- Allowed editors: vi, vim, emacs, Visual Studio Code
- All files should end with a new line
- A `README.md` file at the root of the folder of the project is mandatory
- Code should use the `.js` extension
- Code will be tested using the Jest Testing Framework
- Code will be analyzed using the linter ESLint with specific rules provided
- All functions must be exported

## Setup

### Install NodeJS

To install NodeJS 12.11.x, run the following commands in your home directory:

```sh
curl -sL https://deb.nodesource.com/setup_12.x -o nodesource_setup.sh
sudo bash nodesource_setup.sh
sudo apt install nodejs -y

