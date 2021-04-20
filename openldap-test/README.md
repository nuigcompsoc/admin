# OpenLDAP Docker Image for testing

This image is used by system admin in the CompSoc committee to help them develop software without touching production services.


## Features

* Initialized with data from The Simpsons
* Support for TLS (snake oil cert on build)
* memberOf overlay support


## Usage

```
// docker pull nuigcompsoc/test-openldap
// docker run --rm -p 10389:10389 -p 10636:10636 nuigcompsoc/test-openldap
docker-compose up --build
```

## Exposed ports

* 10389 (ldap)
* 10636 (ldaps)

## Exposed volumes

* /etc/ldap/slapd.d
* /etc/ldap/ssl
* /var/lib/ldap
* /run/slapd


## LDAP structure

### dc=compsoc,dc=ie

| Admin                     | Secret           |
| ------------------------- | ---------------- |
| cn=admin,dc=compsoc,dc=ie | EatMyShorts      |

### ou=people,dc=compsoc,dc=ie

Contains all information on users. Password to every user is their username.

#### uid=hsimpson,ou=people,dc=compsoc,dc=ie
#### uid=msimpson,ou=people,dc=compsoc,dc=ie
#### uid=bsimpson,ou=people,dc=compsoc,dc=ie

### ou=groups,dc=compsoc,dc=ie

| Groups                              |
| ----------------------------------- |
| cn=admin,ou=groups,dc=compsoc,dc=ie |

#### cn=admin,ou=groups,dc=compsoc,dc=ie

| Attribute        | Value                                   |
| ---------------- | --------------------------------------- |
| objectClass      | Group                                   |
| cn               | admin                                   |
| member           | uid=hsimpson,ou=people,dc=compsoc,dc=ie |