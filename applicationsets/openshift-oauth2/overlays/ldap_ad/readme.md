Links

https://docs.redhat.com/en/documentation/openshift_container_platform/4.8/html/authentication_and_authorization/ldap-syncing#ldap-syncing-augmented-activedir_ldap-syncing-groups

https://docs.redhat.com/en/documentation/openshift_dedicated/4/html/authentication_and_authorization/ldap-syncing#ldap-syncing-config-activedir_ldap-syncing-groups

https://docs.redhat.com/en/documentation/openshift_container_platform/4.1/html/authentication/ldap-syncing#ldap-syncing-about_ldap-syncing-groups

https://github.com/openshift/origin/issues/12168

https://docs.redhat.com/en/documentation/openshift_container_platform/4.9/html/authentication_and_authorization/configuring-identity-providers#add-identity-provider_configuring-keystone-identity-provider

https://docs.redhat.com/en/documentation/openshift_container_platform/4.2/html/authentication/ldap-syncing#ldap-syncing-augmented-activedir_ldap-syncing-groups

https://docs.redhat.com/en/documentation/openshift_container_platform/4.2/html/authentication/ldap-syncing#ldap-syncing-activedir_ldap-syncing-groups



kind: LDAPSyncConfig
apiVersion: v1
url: ldaps://...:636
bindDN: CN=binduser,OU=Users,OU=Apps,O=acme
bindPassword: ...
insecure: false
ca: my-ldap-ca-bundle.crt
activeDirectory:
    groupsQuery:
        baseDN: OU=myapp,OU=Apps,O=acme
        scope: sub
        derefAliases: always
        timeout: 0
        filter: (objectClass=group)
        pageSize: 0
    groupUIDAttribute: dn
    groupNameAttributes: [ cn ]
    usersQuery:
        baseDN: "OU=ourcity,OU=FR,OU=Persons,O=acme"
        scope: sub
        derefAliases: never
        filter: (objectclass=inetOrgPerson)
        pageSize: 0
    userNameAttributes: [ uid ]
    groupMembershipAttributes: [ "memberof:1.2.840.113556.1.4.1941:" ]
    tolerateMemberNotFoundErrors: true
    tolerateMemberOutOfScopeErrors: false

