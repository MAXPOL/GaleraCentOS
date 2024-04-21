# GaleraCentOS
GaleraCentOS

After config servers you need start cluster

On first server cluster execute command: galera_new_cluster

On 2 and others servers cluster execute command: systemctl start mariadb

Testsing performance cluster:

On everything servers execute command: mysql -u root -p -e "SHOW STATUS LIKE 'wsrep_cluster_size'"

Answer it should be: wsrep_cluster_size | NUMBER ; Where NUMBER quantity servers in cluster

On any server cluster execute command:

CREATE DATABASE testdb;

CREATE TABLE testdb.testtable ( id INT NOT NULL AUTO_INCREMENT, type VARCHAR(50), quant INT, color VARCHAR(25), PRIMARY KEY(id));

INSERT INTO testdb.testtable (type, quant, color) VALUES ("TestType", 3, "TestColor");'

quit;

On any other server cluster execute command:

mysql -u root -p 

SELECT * FROM testdb.testtable;

quit;

If you received an answer then cluster correct configuration

