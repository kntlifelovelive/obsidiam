
---

## Database Prisma 

#### *Step 1 – Project Initialize*

```bash

mkdir sheets-prisma
cd sheets-prisma
npm init -y
npm install @prisma/client googleapis
npm install prisma --save-dev
npx prisma init


```

#### *Step 2 - `prisma/schema.prisma` config DB type SQLite ပြောင်းပါ*


```bash 

datasource db {
  provider = "sqlite"
  url      = "file:./dev.db"
}

generator client {
  provider = "prisma-client-js"
}


```

#### *Step 3 - Model Define*

*Note - Sheet မှာ Name, Email, Phone လို data ရှိမယ်ဆိုရင် model ကိုရေးပါ*

```js

 model Contact {
   id    Int    @id @default(autoincrement())
   name  String
   email String @unique
   phone String?
 }


```

*And than Command Run inside Project Terminal*

```shell

npx prisma migrate dev --name init

```

**run လိုက်ရင် `dev.db` (SQLite DB) create file**

----

