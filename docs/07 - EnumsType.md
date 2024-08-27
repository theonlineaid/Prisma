In Prisma, you can use enums to define a set of predefined values for a field in your model. Here's how you can incorporate an enum into your Prisma schema:

### Prisma Schema Definition:

```prisma
enum Role {
  ADMIN
  USER
}

model User {
  id    Int    @id @default(autoincrement())
  email String @unique
  name  String @map("firstName")
  role  Role?  @default(USER)  // Note: This line sets the default role to USER

  @@id([email, name])
  @@unique([name, role])
  @@index([id, email])
  @@map("users")
}
```

### Explanation:

- **`enum Role { ADMIN USER }`:**
  - Defines an enum named `Role` with two possible values: `ADMIN` and `USER`.
  - Enums are a way to restrict the values that a field can take. They provide a clear set of options for a field, improving data integrity and clarity.

- **`role Role? @default(USER)`:**
  - The `role` field in the `User` model is of type `Role`, which means it can only be one of the values defined in the `Role` enum.
  - The `?` makes this field optional, meaning it can be `null`.
  - `@default(USER)` sets the default value for the `role` field to `USER` if no value is provided when creating a new `User`.

### Example Records with Enum Values:

1. **User with `ADMIN` Role:**
   ```json
   {
     "id": 1,
     "email": "admin@example.com",
     "name": "Admin User",
     "role": "ADMIN"
   }
   ```
   - This user has the `role` set to `ADMIN`.

2. **User with Default `USER` Role:**
   ```json
   {
     "id": 2,
     "email": "user@example.com",
     "name": "Regular User",
     "role": null
   }
   ```
   - This user has the `role` field set to `null`, which defaults to `USER` due to the `@default(USER)` setting.

### Summary:
- **Enums** define a set of possible values for a field.
- **`@default(USER)`** sets the default value for the `role` field to `USER`.
- The `User` model uses the `Role` enum to restrict the possible values for the `role` field and defaults to `USER` if no value is provided.