---
created: 2026-03-30T09:43
updated: 2026-03-30T09:43
---
It is a way to manage sensitive data. You don't put sensitive info to compose file. Instead, you create a separate file that includes the data.

```
services:
  db:
    image: postgres:latest
    secrets:
      - db_password
    environment:
      - POSTGRES_DB=my_database
      - POSTGRES_PASSWORD_FILE=/run/secrets/db_password # 👈 New line
        
        
secrets:
  db_password:
    file: ./db_password.txt
```


