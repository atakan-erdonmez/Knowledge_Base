---
created: 2026-05-11T15:26
updated: 2026-05-14T11:14
---
# Option 1
You can use `aws login` for temporary, secure access. It directs you to the web browser, authenticating with SSO.

For remote, use `aws login --remote`

# Option 2
You can setup keys. 
1. Create a CLI user in the IAM, give the permissions, save both the keys.
2. On terminal, after installing AWS CLI, run `aws configure` and put keys, region, and default format ('json' is suggested)
3. Test with `aws sts get-caller-identity`