---
tags:
  - "#aws"
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
