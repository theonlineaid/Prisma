# Prisma Setup

```
npm install prisma --save-dev          [Install dev dependency]
npm install @prisma/client
npx prisma init                        [We use NPX version]
npx prisma db pull                     [We use NPX version]

npx prisma migrate dev --name init     [We use NPX version]

npx prisma studio                      [We use NPX version]   [http://localhost:5555]
```

---


```
introspection migration ? 
"prisma": {
    "seed": "ts-node --compiler-options {\"module\":\"CommonJS\"} prisma/seed.ts"
}
```