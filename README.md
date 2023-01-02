# kafka-connect-demo

This project is a demo of how we can produce and consume messages of a kafka topic using avros.

## Getting Started



1. run `docker compose up`
2. Run the commands bellow
```
   docker exec -it kafka-connect-demo-mysql-1 bash
   mysql -uroot -p aurelio -proot
   ALTER USER 'root' IDENTIFIED WITH mysql_native_password BY 'root';
   create table categories (id int auto_increment primary key, name varchar(255));
   insert into categories (name) values('Eletronicos');
```
3. Access [Control Center](http://localhost:9021/)  and Go to `Cluster 1 -> Connect -> connect-default -> Add connector -> Upload connect config file
(Case No Connect Clusters Found then restart kafka-connect container)` and select [mysql.properties](/connectors/mysql.properties)
4. Now you can see the topic `mysql-server.aurelio.categories` responsible for listen our mysql categorie table, select partition 0 and you will see the records that we have inserted in the step 2
5. Access [Control Center](http://localhost:9021/)  and add a new connector [mongodb.properties](/connectors/mongodb.properties)
6. Access [Mongo Express](http://localhost:8085/) and you will see the database `aurelio` click view and you will notice that the records from mysql were migrated to mongodb.




#### Control Center

http://localhost:9021/

#### Mongo Express Interface

http://localhost:8085/