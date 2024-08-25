The `@map` attribute in Prisma is used to map a model field to a column in the database that has a different name. Here's the difference between the two examples you provided:

### 1. **Without `@map`:**
   ```prisma
   model User {
     name String
   }
   ```
   - This defines a `name` field in the `User` model.
   - Prisma will expect a column named `name` in the corresponding database table.
   - If you run migrations, Prisma will create a column named `name` in the `User` table.

### 2. **With `@map`:**
   ```prisma
   model User {
     name String @map("firstName")
   }
   ```
   - This also defines a `name` field in the `User` model.
   - However, Prisma is instructed to map this field to a column named `firstName` in the database.
   - In your Prisma model, you will still refer to this field as `name`, but in the database, it will be stored in a column named `firstName`.

### Summary:
- **Without `@map`:** The field name in your Prisma model matches the column name in the database.
- **With `@map`:** The field name in your Prisma model is different from the column name in the database. The `@map` attribute allows you to use a different name in your Prisma model while mapping it to the correct column in the database.

This feature is helpful when you're working with a database schema that uses different naming conventions, such as snake_case in the database (`first_name`) but camelCase in your Prisma models (`firstName`).