###### Standalone components >

Registramos nosso componente em um módulo qualquer

```ts
//my-module.ts
@NgModule({
  declarations: [HelloWorldComponent],
  imports: [CommonModule, MyModuleRoutingModule],
})
export class MyModule {}

```

```ts
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

<style>
.slidev-code-wrapper  {
  margin-right: 30px;
}

</style>

