###### Standalone components >
O que muda com os standalone components?


````md magic-move

```ts {all}
@Component({
  selector: 'app-hello-world',
  templateUrl: './hello-world.component.html',
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {}

```


```ts {all|4|all}
@Component({
  selector: 'app-hello-world',
  templateUrl: './hello-world.component.html',
  standalone: true,
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {}

```

```ts {all|5|all}
@Component({
  selector: 'app-hello-world',
  templateUrl: './hello-world.component.html',
  standalone: true,
  imports: [],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {}

```

```ts {3}
@Component({
  selector: 'app-hello-world',
  templateUrl: './hello-world.component.html',
  standalone: true,
  imports: [],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {}


```

```ts {3}
@Component({
  selector: 'app-hello-world',
  template: `
   <h1>Hello World</h1>
  `,
  standalone: true,
  imports: [],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {}


```

```ts {all|5-7|14}
@Component({
  selector: 'app-hello-world',
  template: `
   <h1>Hello</h1>
   <ng-container *ngIf="hasPermission">
    <h1>Hello Admin</h1>
   </ng-container>
  `,
  standalone: true,
  imports: [],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {
  hasPermission: boolean = true
}

```

```ts {10}
@Component({
  selector: 'app-hello-world',
  template: `
   <h1>Hello</h1>
   <ng-container *ngIf="hasPermission">
    <h1>Hello Admin</h1>
   </ng-container>
  `,
  standalone: true,
  imports: [NgIf],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {
  hasPermission: boolean = true
}

```

```ts {8}
@Component({
  selector: 'app-hello-world',
  template: `
   <h1>Hello</h1>
   <ng-container *ngIf="hasPermission">
    <h1>Hello Admin</h1>
    <p>{{ strongestPasswordEver$ | async }}</p>
   </ng-container>
  `,
  standalone: true,
  imports: [NgIf],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {
  hasPermission: boolean = true
}

```


```ts {15}
@Component({
  selector: 'app-hello-world',
  template: `
   <h1>Hello</h1>
   <ng-container *ngIf="hasPermission">
    <h1>Hello Admin</h1>
    <p>{{ strongestPasswordEver$ | async }}</p>
   </ng-container>
  `,
  standalone: true,
  imports: [NgIf, AsyncPipe],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {
  hasPermission: boolean = true
  strongestPasswordEver$: Observable<string> = of('@Password2')
}

```

```ts {9}
@Component({
  selector: 'app-hello-world',
  template: `
   <h1>Hello</h1>
   <ng-container *ngIf="hasPermission">
    <h1>Hello Admin</h1>
    <p>{{ strongestPasswordEver$ | async }}</p>
    <app-lazy-multi-select-autocomplete />
   </ng-container>
  `,
  standalone: true,
  imports: [NgIf, AsyncPipe],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {
  hasPermission: boolean = true
  strongestPasswordEver$: Observable<string> = of('@Password2')
}

```

```ts {10|all}
@Component({
  selector: 'app-hello-world',
  template: `
   <h1>Hello</h1>
   <ng-container *ngIf="hasPermission">
    <h1>Hello Admin</h1>
    <p>{{ strongestPasswordEver$ | async }}</p>
    <app-lazy-multi-select-autocomplete />
   </ng-container>
  `,
  standalone: true,
  imports: [NgIf, AsyncPipe, LazyMultiSelectAutocomplete],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {
  hasPermission: boolean = true
  strongestPasswordEver$: Observable<string> = of('@Password2')
}

```

````

