###### Signals >

### Como usar?

````md magic-move

```ts {all}
@Component({
  selector: 'app-hello-world',
  template: `
   <h1>Hello</h1>
  `,
  standalone: true,
  imports: [],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {}

```

```ts {6-6}
@Component({
  selector: 'app-hello-world',
  template: `
   <h1>Hello</h1>
  `,
  standalone: true,
  signals: true,
  imports: [],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {}

```

```ts {7}
@Component({
  selector: 'app-hello-world',
  template: `
   <h1>Hello</h1>
   <p>{{ firstName() }}</p>
   <p>{{ lastName() }}</p>
  `,
  standalone: true,
  signals: true,
  imports: [],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {
  firstName = signal('Jane');
  lastName = signal('Doe');
}

```

```ts {7-8|14-15|all}
@Component({
  selector: 'app-hello-world',
  template: `
   <h1>Hello</h1>
   <p>{{ firstName() }}</p>
   <p>{{ lastName() }}</p>
  `,
  standalone: true,
  signals: true,
  imports: [],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {
  firstName = signal('Jane');
  lastName = signal('Doe');
}

```

```ts {all}
@Component({
  selector: 'app-hello-world',
  template: `
   <h1>Hello</h1>
   <p>{{ firstName.getValue() }}</p>
   <p>{{ lastName | async }}</p>
  `,
  standalone: true,
  signals: true,
  imports: [AsyncPipe],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {
  firstName$ = new BehaviorSubject('Jane');
  lastName$ = new BehaviorSubject('Doe');
}

```

```ts {all}
@Component({
  selector: 'app-hello-world',
  template: `
   <h1>Hello</h1>
   <p>{{ firstName }}</p>
   <p>{{ lastName }}</p>
  `,
  standalone: true,
  signals: true,
  imports: [],
  styleUrls: ['./hello-world.component.scss'],
})
export class HelloWorldComponent {
  firstName ='Jane';
  lastName = 'Doe';
}

```

```ts {all}
@Component({
...
})
export class HelloWorldComponent {
  firstName = signal('Jane');
  lastName = signal('Doe');

  firstName2 ='Jane';
  lastName2 = 'Doe';
  
  firstName$ = new BehaviorSubject('Jane');
  lastName$ = new BehaviorSubject('Doe');
  
  firstName2$ = new Subject();
  lastName2$ = new Subject();

  constructor(){
    this.firstName2$.next('Jane')
    this.lastName2$.next('Doe')
  }
}

```

```ts {all}
@Component({
...
})
export class HelloWorldComponent {
  firstName = signal('Jane');
  lastName = signal('Doe');

  fullName = computed(() => `${this.firstName()} ${this.lastName()}`);

  constructor() {
    effect(() => console.log('Name changed:', this.fullName()));
  }

  setName(newName: string) {
    this.firstName.set(newName);
  }
  
}

```

```ts {all}
@Component({
...
})
export class HelloWorldComponent {
  firstName$ = new BehaviorSubject('Jane');
  lastName$ = new BehaviorSubject('Doe');

  firstName2$ = new Subject();
  lastName2$ = new Subject();

  fullName$  = combineLatest([this.firstName$, this.lastName$]).pipe(map([firstName,lastName] => `${firstName} ${lastName}`))
  fullName2$ = combineLatest([this.firstName$, this.lastName$]).pipe(map([firstName,lastName] => `${firstName} ${lastName}`))

  effect$ = this.fullName$.pipe(tap((fullName)=> console.log('Name changed:', fullName)))

  constructor() {}

  setName(newName: string) {
    this.firstName$.next(newName);
    this.firstName2$.next(newName);
  }
}

```

```ts {all}
@Component({
...
})
export class HelloWorldComponent {
  userService = inject(UserService)
  
  users$: Observable<User[]> = this.userService.getAll() // Observable<User[]>

  users: Signal<Users[]> = toSignal(users$)
  totalUsers: Signal<number> = computed(() => this.users().length);

  constructor() {}
}

```

```ts {all}
@Component({
...
})
export class HelloWorldComponent {
  userService = inject(UserService)
  
  selectedUserId = signal(0)
  selectedUserId$ = toObservable(this.selectedUserId)

  user$ = this.selectedUserId$.pipe(
    filter(Boolean),
    switchMap(id => userService.getUserById(id))
  )

  user = toSignal(user$)
  userHasPermission = !!this.user().permissions.find(p => p === 'ADMIN')

  constructor() {}

  selectUser(id: number) {
    this.selectedUserId.set(id)
  }
}

```

```ts {all}
@Component({
...
})
export class HelloWorldComponent {
  userService = inject(UserService)
  
  selectedUserId$ = new BehaviorSubject<number>(0)

  user$ = selectedUserId$.pipe(
    filter(Boolean),
    switchMap(id => this.userService.getUserById(id))
  )

  userHasPermission$ = this.user$.pipe(map((user)=> !!user.permissions.find(p => p === 'ADMIN')))

  constructor() {}

  selectUser(id: number) {
    this.selectedUserId$.next(id)
  }
}

```


```ts {all}
@Component({
...
})
export class HelloWorldComponent {
   ...

  userHasPermission$ = this.user$.pipe(map((user)=> !!user.permissions.find(p => p === 'ADMIN')))

  constructor() {}

  selectUser(id: number) {
    this.selectedUserId$.next(id)

   if(this.userHasPermission$)  {
    /** do Admin stuff */
   }

   this.userHasPermission$.subscribe(hasPermission => {
    if(hasPermission)  {
      /** do Admin stuff */
    }
   })

  }
}

```

```ts {all}
@Component({
...
})
export class HelloWorldComponent {
   ...

  userHasPermission = !!this.user().permissions.find(p => p === 'ADMIN')

  constructor() {}

  selectUser(id: number) {
    this.selectedUserId$.next(id)

    if(userHasPermission())  {
      /** do Admin stuff */
    }

  }
}

```

````