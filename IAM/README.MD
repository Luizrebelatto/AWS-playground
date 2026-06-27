# AWS Identity And Access Management (IAM)
![IAM Icon](./iamicon.png)

It is an AWS service that allows you to control who can access services and set permission levels for users and services

## Thing you can do with IAM
- Users
- Roles
- Groups
- Policies
- Security Tools

## Users and Groups
Groups are used to manage permissions for different users; users can belong to multiple groups, which makes management easier.
It is not recommended to assign policies to individual users; best practice is to assign them to groups.

![User and Groups Diagram](./usersAndGroups.drawio.png)


## Policies
Policies are Json document that specify what you can and cannot do, for example the group developers has the policie `getListUser` assign so Anyone in the developers group can list the users. You can define user, groups or roles permissions

See below for an example

Policie `IAMReadOnlyAccess` -> users only can see, editing is not allowed

```json
{
    "Version": "2012-10-17",
    "id": 1,
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "iam:GenerateCredentialReport",
                "iam:GenerateServiceLastAccessedDetails",
                "iam:Get*",
                "iam:List*",
                "iam:SimulateCustomPolicy",
                "iam:SimulatePrincipalPolicy"
            ],
            "Resource": "*"
        }
    ]
}
```

#### Structure for Policies

- `version`: Policy language version
- `id`: id for policy(its opcional)
- `statement`: details
- `effect`: permission for the service, can be allow/denied
- `principal`: list of accounts allowed
- `action`: which actions user is allowed to do
- `Resource`: which services user is allowed to do
- `condition`: You can define a condition to run the rules
