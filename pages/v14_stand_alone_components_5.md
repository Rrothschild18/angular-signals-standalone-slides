###### Standalone components >
O que muda na arquitetura de pastas?


````md magic-move


```md {all|8-9}
<!-- Amei simplificado -->
amei-front-gitflow/
│ 
├── src/
│   ├── app/
│   │   ├── auth/
│   │   │   └── ...
│   │   │   └── auth-routing.module.ts
│   │   │   └── auth-module.ts
│   │   │   
│   │   ├── financial/
│   │   ├── home/
│   │   ├── register/
│   │   ├── ...
│   │   ├── ...
│   │   └── waiting-room/
│   │   
│   ├── index.html   <!-- <app-root> </app-root> -->
│   ├── main.ts  <!-- bootstrap pelo AppModule -->
│   └── styles.css  <!-- css das lib -->
│
└── ...config_files


```


```md {8-9}
<!-- Amei simplificado -->
amei-front-gitflow/
│ 
├── src/
│   ├── app/
│   │   ├── auth/
│   │   │   └── ...
│   │   │   └── auth-routing.module.ts ❌
│   │   │   └── auth-module.ts ❌
│   │   │   
│   │   ├── financial/
│   │   ├── home/
│   │   ├── register/
│   │   ├── ...
│   │   ├── ...
│   │   └── waiting-room/
│   │   
│   ├── index.html   <!-- <app-root> </app-root> -->
│   ├── main.ts  <!-- bootstrap pelo AppModule -->
│   └── styles.css  <!-- css das lib -->
│
└── ...config_files

```

```md {8-9}
<!-- Amei simplificado -->
amei-front-gitflow/
│ 
├── src/
│   ├── app/
│   │   ├── auth/
│   │   │   └── ...
│   │   │   └── auth-routes.ts 
│   │   │   
│   │   ├── financial/
│   │   ├── home/
│   │   ├── register/
│   │   ├── ...
│   │   ├── ...
│   │   └── waiting-room/
│   │   
│   ├── index.html   <!-- <app-root> </app-root> -->
│   ├── main.ts  <!-- bootstrap pelo AppModule -->
│   └── styles.css  <!-- css das lib -->
│
└── ...config_files

```




````

