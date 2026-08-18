---
link:
  - "[[00_KnowledgeBase/1- MOCs/AWS]]"
---
[Source](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
[[AWS CLI Setup]],
# Install
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
## Console Credentials (Recommended)
`aws login`

# Setup
## Option 1
You can use `aws login` for temporary, secure access. It directs you to the web browser, authenticating with SSO.

For remote, use `aws login --remote`

## Option 2
You can setup keys. 
1. Create a CLI user in the IAM, give the permissions, save both the keys.
2. On terminal, after installing AWS CLI, run `aws configure` and put keys, region, and default format ('json' is suggested)
3. Test with `aws sts get-caller-identity`