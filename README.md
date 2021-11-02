# Sample Deployment for Alfresco Community with Alfresco Identity Service (AIMS)

**Alfresco Identity Service**, based in Open Source Identity and Access Management [Keycloak](https://www.keycloak.org/), is available for both Community and Enterprise ACS releases.

When using **Alfresco Identity Service**, different [Alfresco Authentication Mechanims](https://docs.alfresco.com/content-services/community/admin/auth-sync/) can be configured.

This project provides a *sample* Docker Compose template for Alfresco Community 7.1 with Alfresco Identity Service 1.6. Note that deploying the product in *production* environments would require additional configuration.

## Docker Compose

Docker Compose template includes following files:

```
.
├── config
│   ├── alfresco-realm.json
│   └── nginx.conf
├── docker-compose.yml
└── search
    └── Dockerfile
```

* `docker-compose.yml` is a regular ACS Docker Compose, including Alfresco Identity Service for Authentication
* `config/alfresco-realm.json` includes a sample configuration for Alfresco Identity Service, since you can create your own configuration using the Keycloak Admin Web Page
* `config/nginx.conf` includes configuration for the NGINX Web Proxy
* `search/Dockerfile` is an extension for Alfresco Search Services Docker Image

## Using

```
$ docker-compose up --build --force-recreate
```

## Service URLs

http://localhost:8080/

ADW
* user: admin
* password: admin

http://localhost:8080/share

Share
* user: admin
* password: admin

http://localhost:8080/alfresco

Alfresco Repository
* user: admin
* password: admin

http://localhost:8999

Kibana
No credentials

**Default configuration for AIMS**

Users

* admin / admin
* test / admin

Roles
* test_role
* default-roles-alfresco

Groups

* admin
* testgroup

## Additional resources

Additional information on Alfresco Identity Service configuration is available in https://docs.alfresco.com/identity-service/latest/

For instance, following properties can be used from `alfresco-global.properties`

```
identity-service.authentication.enabled=
identity-service.enable-basic-auth=
identity-service.authentication.defaultAdministratorUserNames=
identity-service.authentication.validation.failure.silent=
identity-service.auth-server-url=
identity-service.realm=
identity-service.resource=
identity-service.public-client=
identity-service.ssl-required=
identity-service.enable-pkce=
identity-service.credentials.secret=
identity-service.credentials.provider=
```

Tutorials on how to configure different Authetication Subsystems are available in:

* https://docs.alfresco.com/identity-service/latest/tutorial/sso/saml/
* https://docs.alfresco.com/identity-service/latest/tutorial/sso/ldap/
* https://docs.alfresco.com/identity-service/latest/tutorial/sso/kerberos/

## Related projects

If you want to discover some other features that can be used with Keycloak, check this Community project:

https://github.com/Acosix/alfresco-keycloak

Additional details are provided by [@AFaust](https://github.com/afaust) in TTL #133: https://www.alfresco.com/events/webinars/tech-talk-live-133
