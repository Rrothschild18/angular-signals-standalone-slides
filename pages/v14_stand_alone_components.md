###### Standalone components >

### Normalmente fazemos componentes como


No terminal:

```bash
ng g c my-module/hello-world

```
<br>
<details>
  <summary>hello-world.componet.ts</summary>

```ts
@Component({
  selector: 'app-hello-world',
  templateUrl: './hello-world.component.html',
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {
  /** Aqui a mae chora e filho ve */
}

```
</details>


<details>
  <summary>hello-world.component.html</summary>

```html
<p>your spaghetti component works!</p>

```
</details>


<details>
  <summary>hello-world.scss</summary>


```scss
.HelloWorld {
  z-index: OVER_9000_PRESS_F;
  background: red !important;
  position: absolute;
  top: 0;
  rigth: 0;
  rihgt: 0;
  raigth: 0;
}

```
</details>


<details>
  <summary>hello-world.component.spec.ts</summary>

```ts
// Aqui ngm liga
// Só faz teste quem não se garante na Força Tarefa

describe('HelloWorldComponent', () => {
  let component: HelloWorldComponent;
  let fixture: ComponentFixture<HelloWorldComponent>;
  //...
  it('should explode', () => {
    expect(component).toBeTruthy();
  });
})

```
</details>

