The `@@map` attribute in Prisma is used to map a Prisma model to an existing table in your database with a different name. In the example you provided, the `@@map("users")` directive tells Prisma to map the `User` model to the `users` table in the database.

### Explanation:

1. **Without `@@map`:**
   ```prisma
   model User {
     id    Int    @id 
     email String @unique
     name  String 
     role  String
   }
   ```
   - This defines a `User` model.
   - Prisma will expect a table named `User` in your database by default.
   - If you run migrations, Prisma will create a table named `User`.

2. **With `@@map`:**
   ```prisma
   model User {
     id    Int    @id 
     email String @unique
     name  String 
     role  String

     @@map("users")
   }
   ```
   - This also defines a `User` model.
   - However, Prisma is instructed to map this model to an existing table named `users` in the database.
   - This is useful if you already have a table named `users` in your database, or if you want to use a different table name in your database but still use the `User` model in your code.

### Summary:
- The `@@map` attribute allows you to keep your Prisma model names clean and consistent in your code while adapting to different table names in your database.
- If you omit `@@map`, Prisma assumes the table name in the database matches the model name.
- If you include `@@map`, you can specify a different table name in the database.

This is particularly useful in scenarios where you're working with a legacy database or an existing database schema where table names don't follow the conventions you'd like to use in your Prisma models.