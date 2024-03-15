###### Standalone components >
O que muda com os standalone components?


````md magic-move


```ts {all}
//my-routing-module.ts
export const routes: Routes = [
  {
    path: '👉👈',
    component: HelloWorldComponent
  },
];

@NgModule({
  declarations: [],
  imports: [CommonModule, RouterModule.forChild(routes)],
  exports: [RouterModule],
})
export class MyRoutingModule {}

```

```ts {5-8}
//my-routing-module.ts
export const routes: Routes = [
  {
    path: '👉👈',
    loadComponent: () =>
      import('./path/to/hello-world.component').then(
        (cmp) => cmp.HelloWorldComponent,
      ),
  },
];

@NgModule({
  declarations: [],
  imports: [CommonModule, RouterModule.forChild(routes)],
  exports: [RouterModule],
})
export class MyRoutingModule {}

```

```ts {10-16}
//my-routing-module.ts
export const routes: Routes = [
  {
    path: '👉👈',
    loadComponent: () =>
      import('./path/to/hello-world.component').then(
        (cmp) => cmp.HelloWorldComponent,
      ),
  },
  {
    path: '🪲🪲',
    loadChildren: () =>
      import('./path/to/other-routing.module').then(
        (m) => m.BugModule,
      ),
  },
];
...
@NgModule({
  declarations: [],
  imports: [CommonModule, RouterModule.forChild(routes)],
  exports: [RouterModule],
})

```

````

