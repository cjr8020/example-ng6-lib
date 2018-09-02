# ExampleNg6LibTestApp

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 6.1.5.

based on [article](https://blog.angularindepth.com/creating-a-library-in-angular-6-87799552e7e5)


	In angular 6, angular.json represents what is now called a 'workspace'
	with possibly multiple projects.


Plan:
-----

- create a workspace with the same name as the intended library: `example-ng6-lib`
- in the same workspace, generate a test application for this library named `example-ng6-lib-test-app`
- in the same workspace, generate an Angular library named `example-ng6-lib`
- the library will have a prefix `enl` (**e**xample **n**g6-**l**ibrary)
- the library will be tested by importing it into `example-ng6-lib-test-app` test application.



#### create new angular workspace with 

```
$ ng new example-ng6-lib-test-app
$ mv example-ng6-lib-test-app example-ng6-lib
```

The reason for this is to create the test app right away, but then rename the repository folder 
so that it is named to correspond to the name of the library we are generating. 

Resulting structure:

```
example-ng6-lib/
  e2e/
  src/
    app/
      [this is our test-app]
    assets/
    environments/
    index
    karma.conf.js
    .
    .
    .
```


Next, generate the library itself:

```
$ ng generate library example-ng6-lib --prefix=enl
```
note: by default, the CLI will use `lib` prefix.

```
CREATE projects/example-ng6-lib/karma.conf.js (968 bytes)
CREATE projects/example-ng6-lib/ng-package.json (191 bytes)
CREATE projects/example-ng6-lib/ng-package.prod.json (164 bytes)
CREATE projects/example-ng6-lib/package.json (175 bytes)
CREATE projects/example-ng6-lib/tsconfig.lib.json (769 bytes)
CREATE projects/example-ng6-lib/tsconfig.spec.json (246 bytes)
CREATE projects/example-ng6-lib/tslint.json (317 bytes)
CREATE projects/example-ng6-lib/src/public_api.ts (191 bytes)
CREATE projects/example-ng6-lib/src/test.ts (700 bytes)
CREATE projects/example-ng6-lib/src/lib/example-ng6-lib.module.ts (261 bytes)
CREATE projects/example-ng6-lib/src/lib/example-ng6-lib.component.spec.ts (679 bytes)
CREATE projects/example-ng6-lib/src/lib/example-ng6-lib.component.ts (281 bytes)
CREATE projects/example-ng6-lib/src/lib/example-ng6-lib.service.spec.ts (418 bytes)
CREATE projects/example-ng6-lib/src/lib/example-ng6-lib.service.ts (142 bytes)
UPDATE angular.json (4979 bytes)
UPDATE package.json (1565 bytes)
UPDATE tsconfig.json (566 bytes)
```


Outcome: 

- new `example-ng6-lib` project added to angular.json and project structure
- `ng-packagr` dependencies added to `package.json`

```
  "devDependencies": {
    ...
    "@angular-devkit/build-ng-packagr": "~0.7.0",
    "ng-packagr": "^3.0.0",
    "tsickle": ">=0.29.0",
    "tslib": "^1.9.0",    
    ...
```

- reference to `example-ng6-lib` build path is added to `tsconfig.json`:

```
    "paths": {
      "example-ng6-lib": [
        "dist/example-ng6-lib"
      ],
      "example-ng6-lib/*": [
        "dist/example-ng6-lib/*"
      ]
    }
```

Resulting structure:

```
example-ng6-lib/
  e2e/
  
  projects/             <-- this is added
    example-ng6-lib/
      src/
        lib/
          example-ng6-lib.component.spec.ts
          example-ng6-lib.component.ts
          example-ng6-lib.module.ts
          example-ng6-lib.service.spec.ts
          example-ng6-lib.service.ts
        public_api.ts
        tests.ts
      karma.conf.js
      ng-package.json
      ng-package.prod.json
      package.json
      tsconfig.lib.json
      tsconfig.spec.json
      tslint.json
      
  src/
    app/
      [this is our test-app]
    assets/
    environments/
    index
    karma.conf.js
    .
    .
    .
```



## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).
