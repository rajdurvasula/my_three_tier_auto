# my_three_tier_auto

Purpose of this project is to demonstrate ansible automated deployment of a 3-tier application

## Roles
The following ansible roles are created in this project:

- rd_ans_common: Installs common OS packages using yum
- rd_config_app_db: Configures application database objects
- rd_config_http: Configures static web pages on Apache HTTP
- rd_config_haproxy: Configures HAProxy to proxy to Apache Tomcat instances
- rd_config_tomcat: Configures Apache Tomcat
- rd_install_haproxy: Installs HAProxy
- rd_install_tomcat: Installs Apache Tomcat
- rd_setup_dbclient: Installs PostgreSQL JDBC driver

## Usage:

ansible-playbook -i myinventory.file main.yml --ask-vault-pass

### Configuration requirements for AWS EC2 Deployments:
- Need to manually set Security Group Inbound Rules
  - Allow 80 to your Public IP address. This will allow you test Frontend URL
  - Allow 8080 limited to your Frontend Host access to App Host
  - Allow 5432 limited to your App Host access to DB Host

### Vault password is required to copy YUM repository settings
- Password: passw0rd

## Default configurations:
- PostgreSQL admin user: postgres
- PostgreSQL admin password: passw0rd
- PostgreSQL Application Database: empdb
- PostgreSQL Application user: guest1
- PostgreSQL Application password: passw0rd
- Tomcat Admin user: admin
- Tomcat Admin password: admin
