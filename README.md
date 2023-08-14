# Docker-compose for MySQL
This docker-compose file is for spinning up MySQL server 8.0 with utf8mb4.

# Precondition 
- Docker installed
- Docker compose installed
  
# Usage
1. Clone this repo
2. Run `docker-compose up --build`

# How to set up the default tables
Please see `db/mysql_init/01-databases.sql` and add tables accordingly.

# How to cleanup the environment.
1. Delete `db/mysql_data`
2. Run `docker-compose down --rmi all --volumes --remove-orphans`

### Memos:
 - Set all services in same docker v-network (name : mysql-lf-network)
 - Use docker's command to check v-network's status
    ```
     docker network ls
     docker network inspect ${network name}
    ```
