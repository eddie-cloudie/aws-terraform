# Create iam user in AWS CLI

- `aws configure`
`AWS Access Key ID [****************HTHS]: AKIA3PQL***********`
`AWS Secret Access Key [****************Y2bu]: oVjvG**********`
`Default region name [ap-southeast-2]: ap-southeast-4`
`Default output format [json]: json`

## verify aws credentials

- `cat ~/.aws/credentials`
`[default]`
`aws_access_key_id = AKIA3PQL***********`
`aws_secret_access_key = oVjvG**********`

## verify iam user

- `aws iam get-user`
`{
    "User": {
        "UserName": "eddie-c",
        "UserId": "789*********",
        "Arn": "arn:aws:iam::789********",
        "CreateDate": "2026-09-03T04:35:34+00:00",
        "PasswordLastUsed": "2026-09-03T04:47:28+00:00"
    }
}`

## create iam user 
- `aws iam create-user --user-name dev_terraform`
`{
    "User": {
        "Path": "/",
        "UserName": "dev_terraform",
        "UserId": "AIDA3PQLA5GFADFSZE5XM",
        "Arn": "arn:aws:iam::789********:user/dev_terraform",
        "CreateDate": "2026-09-03T12:54:36+00:00"
    }`
## attach policy
- `aws iam attach-user-policy \
 --user-name dev_terraform \
 --policy-arn arn:aws:iam::aws:policy/PowerUserAccess`

## verify policy
- `aws iam list-attached-user-policies --user-name dev_terraform`
`{
    "AttachedPolicies": [
        {
            "PolicyName": "PowerUserAccess",
            "PolicyArn": "arn:aws:iam::aws:policy/PowerUserAccess"
        }
    ]
}`

