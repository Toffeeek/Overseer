# Overseer (fuck azam and fuck shohel)

## 1. Database instructions

### 1.1 Create the database:
```
CREATE ROLE overseer_owner LOGIN;
\password overseer_owner
CREATE DATABASE overseer OWNER overseer_owner;
```

### 1.2 Login:
```
psql -h 127.0.0.1 -U overseer_owner -d overseer
```

### 1.3 Import functions:
Run this outside the psql terminal when starting your work to import the functions teammates have written
```
psql -h 127.0.0.1 -U overseer_owner -d overseer \
  -v ON_ERROR_STOP=1 -f server/db/routines.sql
```

### 1.4 Migrate contributions:
Run this outside the psql terminal when you are make changes to the database
```
mkdir -p server/db/migrations
pg_dump -h 127.0.0.1 -U overseer_owner -d overseer --no-owner --no-privileges > server/db/<commit-name>.sql
```
