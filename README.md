# HTTP-Ng-WordPress-API
## Angular 5 + WordPress API intergration 
### For using Angular in the Front-end & WordPress for Back-end development.
#### GET request to fetch posts (10) from WordPress and display in Angular 5.
This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 1.6.7.

#### app.module.ts
```javascript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { HttpClientModule } from '@angular/common/http';
import { AppComponent } from './app.component';


@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    HttpClientModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

```

#### app.component.ts
```javascript
import { Component, OnInit } from '@angular/core';
import { HttpClient } from '@angular/common/http';
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent implements OnInit {
  posts = [];

  constructor(private http: HttpClient) {}

  ngOnInit(): void {
     this.http.get('https:YOUR SITE/wp-json/wp/v2/posts').subscribe(data => {
       for (const key in data) {
         if (data.hasOwnProperty(key)) {
           this.posts.push(data[key]);
         }
       }
       console.log(this.posts);
     });

  }
}

```

#### app.component.html
```javascript
<h1>Angular 5 & WordPress API</h1>

<ul>

    <li *ngFor="let post of posts">
        <h2>
            <div [innerHTML]="post.title.rendered"></div>
        </h2><br>

        <div class="subtitle" [innerHTML]="post.excerpt.rendered"></div>
        <div [innerHTML]="post.content.rendered"></div>

        <p>{{post.date}}</p>

    </li>

</ul>
```

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `-prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).
# Angular-5-WordPress-API
