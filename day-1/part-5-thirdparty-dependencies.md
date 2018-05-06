# Part 5 - Thirdparty dependencies

<<<<<<< Updated upstream:day-1/part-5-thirdparty-dependencies.md
![](https://github.com/duncanhunter/Enterprise-Angular-Applications-With-NgRx-and-Nx-Book/tree/c180ff2f255906954d2a81055d876d57bfe05508/assets/material-site.png)
=======
<<<<<<< HEAD:part-5-thirdparty-dependencies.md
![](.gitbook/assets/material-site.png)
=======
![](https://github.com/duncanhunter/Enterprise-Angular-Applications-With-NgRx-and-Nx-Book/tree/c180ff2f255906954d2a81055d876d57bfe05508/assets/material-site.png)
>>>>>>> 27deda11f6fd2bafdd4d7805be1cb52bb774afc8:day-1/part-5-thirdparty-dependencies.md
>>>>>>> Stashed changes:day-1/part-5-thirdparty-dependencies.md

[https://material.angular.io/](https://material.angular.io/)

## 1.Install angular material, angular animations and angular flex layout

```text
npm install --save @angular/material @angular/cdk @angular/flex-layout @angular/animations
```

* Add animations module to the main app module.

```typescript
import {BrowserAnimationsModule} from '@angular/platform-browser/animations';

@NgModule({
  ...
  imports: [BrowserAnimationsModule],
  ...
})
export class AppModule { }
```

## 2.Add a new nx lib to hold all the common material components we will use in our app

```text
ng g lib material
```

* Add all the common material components and re-export them

_**libs/material/src/material.module.ts**_

```typescript
import { NgModule } from '@angular/core';
import { FlexLayoutModule } from '@angular/flex-layout';

import {
  MatInputModule,
  MatCardModule,
  MatButtonModule,
  MatSidenavModule,
  MatListModule,
  MatIconModule,
  MatToolbarModule,
  MatProgressSpinnerModule,
  MatMenuModule,
  MatTableModule,
  MatSelectModule
} from '@angular/material';

@NgModule({
  imports: [
    FlexLayoutModule,
    MatInputModule,
    MatCardModule,
    MatButtonModule,
    MatSidenavModule,
    MatListModule,
    MatIconModule,
    MatToolbarModule,
    MatProgressSpinnerModule,
    MatMenuModule,
    MatTableModule,
    MatSelectModule
  ],
  exports: [
    FlexLayoutModule,
    MatInputModule,
    MatCardModule,
    MatButtonModule,
    MatSidenavModule,
    MatListModule,
    MatIconModule,
    MatToolbarModule,
    MatProgressSpinnerModule,
    MatMenuModule,
    MatTableModule,
    MatSelectModule
  ]
})
export class MaterialModule {}
```

* Add material module to auth module

_**libs/auth/src/auth.module.ts**_

```typescript
import { MaterialModule } from '@demo-app/material';

@NgModule({
  ...
imports: [CommonModule, RouterModule, HttpClientModule, MaterialModule],
  ...
})
export class AuthModule { }
```

## 3. Add material default styles

_**apps/customer-portal/src/styles.scss**_

```css
@import '~@angular/material/prebuilt-themes/deeppurple-amber.css';
```

* Update the login-form to use material components

_**libs/auth/src/components/login-form/login-form.component.html**_

```markup
<mat-card>
    <mat-card-title>Login</mat-card-title>
    <mat-card-content>
        <form fxLayout="column" fxLayoutAlign="center none">
            <mat-input-container>
                <input matInput placeholder="username" type="text" #username>
            </mat-input-container>
            <mat-input-container>
                <input matInput placeholder="password" type="text" #password>
            </mat-input-container>
        </form>
        <button mat-raised-button (click)="login({username:username.value, password:password.value})">login</button>
    </mat-card-content>
</mat-card>
```

## 4. Go and explore flex layout docs

[https://tburleson-layouts-demos.firebaseapp.com/\#/docs](https://tburleson-layouts-demos.firebaseapp.com/#/docs)
