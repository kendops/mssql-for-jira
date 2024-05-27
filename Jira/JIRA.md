```sh
### To Install Jira 
helm upgrade -i jira atlassian-data-center/jira --namespace jira --create-namespace --values jira-values.yaml 
  
# --set persistence.storageClass=gp3

kubectl get pod -n jira
kubectl get svc -n jira
kubectl get ing -n jira
kubectl describe pod jira-0 -n jira 

### To uninstall Jira 
helm uninstall jira -n jira
kubectl delete ns jira 
kubectl get ns

### README
### Deploy Amazon RDS databases for applications in Kubernetes
https://aws.amazon.com/blogs/database/deploy-amazon-rds-databases-for-applications-in-kubernetes/

### Deploy JIRA
https://atlassian.github.io/data-center-helm-charts/userguide/INSTALLATION/

Vendor         | JDBC driver class                             |  Example JDBC URL
------------------------------------------------------------------------------------------------------------------------
PostgreSQL     | org.postgresql.Driver                         |  jdbc:postgresql://<dbhost>:5432/<dbname>
MySQL          | com.mysql.jdbc.Driver                         |  jdbc:mysql://<dbhost>/<dbname>
SQL Server     | com.microsoft.sqlserver.jdbc.SQLServerDriver  |  jdbc:sqlserver://<dbhost>:1433;databaseName=<dbname>
Oracle         | oracle.jdbc.OracleDriver                      |  jdbc:oracle:thin:@<dbhost>:1521:<SID>

####################################################################

database:
  type: <db_type>
  url: <jdbc_url>
  driver: <engine_driver>
  credentials:
    secretName: <secret_name>
    usernameSecretKey: username
    passwordSecretKey: password

####################################################################
```