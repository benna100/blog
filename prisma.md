# Prisma



## Connection string

https://www.prisma.io/docs/concepts/database-connectors/mysql



## Migration

npx prisma migrate dev --name init



## Seeding

 npx prisma db seed



Add this to package.json



```
,
  "prisma": {
    "seed": "node prisma/seed.js"
  }
```

