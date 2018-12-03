<p align="center"><img src="https://avatars1.githubusercontent.com/u/41109786?s=200&v=4"/></p>
<p align="center">
    <a href="https://travis-ci.org/nestjs-community/nestjs-flub"><img src="https://travis-ci.org/nestjs-community/nestjs-flub.svg?branch=master"/></a>
    <a href="https://www.npmjs.com/package/nestjs-flub"><img src="https://img.shields.io/npm/v/nestjs-flub.svg"/></a>
    <a href="https://github.com/nestjs-community/nestjs-flub/blob/master/LICENSE"><img src="https://img.shields.io/github/license/nestjs-community/nestjs-flub.svg"/></a>
    <a href='https://coveralls.io/github/nestjs-community/nestjs-flub?branch=master'><img src='https://coveralls.io/repos/github/nestjs-community/nestjs-flub/badge.svg?branch=master' alt='Coverage Status' /></a>
    <a href="https://greenkeeper.io/"><img src="https://badges.greenkeeper.io/shekohex/nestjs-flub.svg"/></a>
</p>
<h1 align="center">Nestjs Flub</h1>

Pretty ErrorHandler 😫, Stack Viewer for [Nestjs Framework](https://nestjs.com/) 🛠️
> it's just a simple `Filter` for Catching the Errorrs

## Features

1. HTML reporter

2. JSON reporter, if request accepts a json instead of text/html.

3. Sorted frames of error stack.

4. Themes


### Dark Theme
![dark](https://files.gitter.im/nestjs/nestjs/qkqB/error-dark.png)

### Light Theme
![light](https://files.gitter.im/nestjs/nestjs/z6X6/error-light.png)

## Install

```bash
npm install nestjs-flub --save
```

## Simple Usage
Just add this filter as you used to add any filters
```typescript
import { FlubErrorHandler } from 'nestjs-flub';
@Controller('cats')
@UseFilters(new FlubErrorHandler())
export class CatsController { 

@Get('/error')
  throwError() {
    throw new Error('Very Bad Error');
  }
}

```

## Configuration 
 **FlubErrorHandler** accepts an object as an options to configure the Error Handler </br>
 for now it only have to Options
 ```typescript
theme: string; // for themes ['dark', 'light', 'default']
quote: boolean; // for displaying  very good quotes
 ```
 example
 
 ```typescript
 @UseFilters(new FlubErrorHandler({ theme: 'dark', quote:true }))
 ```
 #### Theming
 
 copy `/src/themes/error.default.mustache` and play
 
 ## TODO 
 - [ ] Write Tests
- [ ] list syntax required

 ## Contributing

you are welcome with this project for contributing,
If you have new themes just make a new PR with and simple image for the theme

## Global filters 

Use flub error handler for all controllers 

```typescript 
async function bootstrap() {
  const app = await NestFactory.create(ApplicationModule);
  app.useGlobalFilters(new FlubErrorHandler());
  await app.listen(3000);
}
bootstrap();