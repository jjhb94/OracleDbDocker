# Setup:
### 1. Install docker, run it, and then pull th latest image from docker!
- docker pull container-registry.oracle.com/database/express:latest
- If you don’t have an Oracle account, you’ll need to create one and accept the license agreement for the image.

### 2. Run Two Oracle Database Containers:
- You’ll need to run two separate containers, each with its own database instance. Use different ports and container names to distinguish them.
### in bash:
- First Oracle database:
```
docker run -d \
  --name oracle_db1 \
  -p 1521:1521 \
  -e ORACLE_PWD=your_password \
  container-registry.oracle.com/database/express:latest
```
- Second Oracle database:
```
docker run -d \
  --name oracle_db2 \
  -p 1522:1521 \
  -e ORACLE_PWD=your_password \
  container-registry.oracle.com/database/express:latest
  ```
### 3. Verify db's are running :o
- Check the logs to ensure the databases are up and running:
### in bash: 
````
docker logs -f oracle_db1
docker logs -f oracle_db2
````

### 4. Connect to the Databases:
- You can connect to the databases using the following connection strings:
````
For oracle_db1: User Id=system;Password=your_password;Data Source=localhost:1521/XEPDB1

For oracle_db2: User Id=system;Password=your_password;Data Source=localhost:1522/XEPDB1
````
- Use a tool like SQL*Plus, Oracle SQL Developer, or DBeaver to test the connections.