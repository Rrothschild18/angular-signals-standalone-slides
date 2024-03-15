###### Standalone components >
O que muda nas rotas do antigo app-module.ts?


````md magic-move

```ts {all|14-17}
//main.ts
...

setupLogCrash();

if (
  environment.envType != EnvTypes.LOCAL &&
  environment.envType != EnvTypes.DEVELOPMENT &&
  environment.envType != EnvTypes.QA
) {
  enableProdMode();
}

platformBrowserDynamic()
  .bootstrapModule(AppModule)
  .catch((err) => logCrash(err));

```

```ts {all}
//main.ts
bootstrapApplication(AppComponent, appConfig).catch((err) =>
  console.error(err)
);

```

```ts {all|6-18}
//app-config.ts
export const appConfig: ApplicationConfig = {
  providers: [
    provideRouter(routes, withComponentInputBinding()),
    provideAnimations(),
    importProvidersFrom(
      NgxsModule.forRoot([
        ...
        LayoutState,
        UserState,
        ProcedureMetaState,
        BankMetaState,
        ProviderMetaState,
        AttendancePlaceMetaState,
        BankMetaState,
        ...
      ]),
    ),
  ],
};

```


```ts {all|11-21}
//app-config.ts
export const appConfig: ApplicationConfig = {
  providers: [
    provideRouter(routes, withComponentInputBinding()),
    provideAnimations(),
    importProvidersFrom(
      NgxsModule.forRoot([
        ...
      ]),

     //Library Modules
      SocketIoModule.forRoot(config),
      BrowserAnimationsModule
      NgxDatatableModule,
      NgxMaskModule.forRoot(options),
      NgxDropzoneModule,
      CalendarModule.forRoot({
       provide: DateAdapter,
       useFactory: adapterFactory,
      }),
    ),
    provideHttpClient(withInterceptors([TokenInterceptor])),
  ],
};

```

```ts {all|14-19}
//app-config.ts
export const appConfig: ApplicationConfig = {
  providers: [
    provideRouter(routes, withComponentInputBinding()),
    provideAnimations(),
    importProvidersFrom(
      NgxsModule.forRoot([
        ...
      ]),

      //Library Modules
      ...

      //Providers
      { provide: LOCALE_ID, useValue: 'pt-BR' },
      { provide: MAT_DATE_LOCALE, useValue: 'pt-BR' },
      { provide: DEFAULT_CURRENCY_CODE, useValue: 'BRL' },
      { provide: ErrorHandler, useClass: AmeiErrorHandler },
    ),
    provideHttpClient(withInterceptors([TokenInterceptor])),
  ],
};

```

````

