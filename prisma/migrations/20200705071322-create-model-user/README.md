# Migration `20200705071322-create-model-user`

This migration has been generated by Manny at 7/5/2020, 7:13:22 AM. You can
check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql
CREATE TABLE "public"."User" (
"confirmation_token" text  NOT NULL ,"confirmed_at" timestamp(3)   ,"created_at" timestamp(3)  NOT NULL DEFAULT CURRENT_TIMESTAMP,"email" text  NOT NULL ,"first_name" text  NOT NULL ,"id" text  NOT NULL ,"last_name" text  NOT NULL ,"password" text  NOT NULL ,"refresh_token" text   ,"reset_token" text   ,"updated_at" timestamp(3)  NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY ("id"))

CREATE UNIQUE INDEX "User.email" ON "public"."User"("email")
```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration 20200704130613-init-database..20200705071322-create-model-user
--- datamodel.dml
+++ datamodel.dml
@@ -2,10 +2,24 @@
 // learn more about it in the docs: https://pris.ly/d/prisma-schema
 datasource db {
   provider = "postgresql"
-  url = "***"
+  url = "***"
 }
 generator client {
   provider = "prisma-client-js"
 }
+
+model User {
+  id                 String    @default(uuid()) @id
+  first_name         String
+  last_name          String
+  email              String    @unique
+  password           String
+  reset_token        String?
+  refresh_token      String?
+  confirmation_token String
+  confirmed_at       DateTime?
+  created_at         DateTime  @default(now())
+  updated_at         DateTime  @default(now())
+}
```
