###### Standalone components >
O que muda nas rotas do antigo app-routing.module.ts?


````md magic-move

```ts {all}
//auth-routes.ts
export const AUTH_ROUTES: Routes = [
  {
    path: '',
    component: AuthComponent,
    children: [
      {
        path: '',
        redirectTo: 'login',
        pathMatch: 'full',
      },
      {
        path: 'login',
        loadComponent: () => import('.../.../').then((cmp) => cmp.LoginComponent)
      },
      {
        path: 'forgot-password',
        loadComponent: () => import('.../.../').then((cmp) => cmp.ForgotPasswordComponent)
      },
      ...
    ],
  },
];
```


```ts {all|5-9}
//app-routes-module.ts
export const routes: Routes = [
  {
    path: 'auth',
    loadChildren: () => import('./auth/auth.routes').then((r) => r.AUTH_ROUTES),
  },
 ...
];
```

```ts {all|7-11}
//app-routes-module.ts
export const routes: Routes = [
  {
    path: 'auth',
    loadChildren: () => import('./auth/auth.routes').then((r) => r.AUTH_ROUTES),
  },
  {
    path: 'auth',
    loadChildren: () => import('./auth/auth.module').then((m) => m.AuthModule),
  },
];
```

````

