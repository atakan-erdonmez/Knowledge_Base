---
link:
  - "[[AWS]]"
---
[Source](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

# Install
---
## Linux
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

**To update current installation**:
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install --bin-dir /usr/local/bin --install-dir /usr/local/aws-cli --update
```

## Windows
https://awscli.amazonaws.com/AWSCLIV2.msi

# Login
---
## Option 1
You can use `aws login` for temporary, secure access. It directs you to the web browser, authenticating with SSO.

For remote, use `aws login --remote`

## Option 2
You can setup keys. 
1. Create a CLI user in the IAM, give the permissions, save both the keys.
2. On terminal, after installing AWS CLI, run `aws configure` and put keys, region, and default format ('json' is suggested)
3. Test with `aws sts get-caller-identity`

## Other Methods & Comparison

| Method                                | Credentials                                          | Expire?                 | Best for                          |
| ------------------------------------- | ---------------------------------------------------- | ----------------------- | --------------------------------- |
| `aws configure`                       | Access Key + Secret Key                              | ❌ Usually long-lived    | Legacy/simple IAM-user setups     |
| `aws configure sso` + `aws sso login` | IAM Identity Center / SSO                            | ✅ Temporary             | Organizations / multiple accounts |
| `aws login`                           | Your AWS Console credentials → temporary credentials | ✅ Up to 12h             | Personal/local development        |
| IAM Role on EC2                       | Instance metadata credentials                        | ✅ Automatically rotated | AWS workloads                     |
| Environment variables                 | Whatever credentials you provide                     | Depends                 | CI/CD, temporary sessions         |
