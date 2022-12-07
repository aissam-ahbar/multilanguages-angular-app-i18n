# Make Angular Application multi-languages with i18n ngx-translate translate pipe [![Build Status](https://travis-ci.org/ngx-translate/core.svg?branch=master)](https://codingjobs-77e8f.web.app/jobs/2)[![npm version](https://d25lcipzij17d.cloudfront.net/badge.svg?id=js&r=r&type=6e&v=0.0.1&x2=0)](https://codingjobs-77e8f.web.app/jobs/2)

This app is a demo showing how to perform translation on your angular app in many languages. We use the internationalization (i18n) library for Angular.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [More courses with @CodingJobs by Artificial Intelligence](https://codingjobs-77e8f.web.app/jobs/2)

## Installation

First you need to install the following dependencies using Node Package Manager (npm) :

```sh
npm install @ngx-translate/core
npm install @ngx-translate/http-loader
```

## Setup Modules & Components

#### 1. Setup your translation in ./assets/i18n

- fr.json
- en.json

You can then access the value by using the dot notation, for example `HOME.TITLE` :

```json
{
  "HOME": {
    "TITLE": "Hello world by Aissam !"
  }
}
```

#### 2. Import Modules, factory and HttpClient

```ts
// AoT requires an exported function for factories
export function HttpLoaderFactory(httpClient: HttpClient) {
  return new TranslateHttpLoader(httpClient);
}

@NgModule({
  declarations: [AppComponent],
  imports: [
    BrowserModule,
    HttpClientModule,
    // Import translate module and factory
    TranslateModule.forRoot({
      loader: {
        provide: TranslateLoader,
        useFactory: HttpLoaderFactory,
        deps: [HttpClient],
      },
    }),
  ],
  bootstrap: [AppComponent],
})
export class AppModule {}
```

#### 3. Define the `default language` for the application

```ts
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css'],
})
export class AppComponent {
  constructor(translate: TranslateService) {
    const language = 'en';
    translate.use(language);
  }
}
```

#### 4. Use the translation on your HTML Template for render on the fly

```html
<div>{{ 'HOME.TITLE' | translate }}</div>
```

## Additional Angular Courses with Coding Jobs

- [Angular @CodingJobs by Artificial Intelligence ](https://codingjobs-77e8f.web.app/jobs/2)
