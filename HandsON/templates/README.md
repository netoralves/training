# Deploy Openshift
Example template to deploy ephemeral mySQL Pod and famous-quote app to load database. This template use arm64 architecture.

## Create project and template
```
oc new-project famous
```

```
oc create -f famous-template.yaml
template.template.openshift.io/famous created

```

```
oc get template
NAME     DESCRIPTION   PARAMETERS        OBJECTS
famous                 8 (1 generated)   5

```

## Deploy app

```
oc new-app --template=famous-app -p NAME=quotes

--> Deploying template "famous/famous" to project famous

     * With parameters:
        * Nome=quotes
        * Plugin de autenticacao MySQL=mysql_native_password
        * Versao MySQL=8.0-el8
        * Database Service Name=mysql
        * Nome do Banco de Dados=famousdb
        * Usuario do Banco de Dados=dbfamoususer
        * Senha do Banco de Dados=LeQ873wPf62tHvwn # generated
        * Namespace=openshift

--> Creating resources ...
    secret "quotes" created
    service "mysql" created
    service "quotes" created
    deploymentconfig.apps.openshift.io "quotes" created
    deploymentconfig.apps.openshift.io "mysql" created
--> Success
    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:
     'oc expose service/mysql'
     'oc expose service/quotes'
    Run 'oc status' to view your app.

```
