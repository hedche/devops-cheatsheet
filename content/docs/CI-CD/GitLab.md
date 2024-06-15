---
title: GitLab
type: docs
prev: docs/first-page
next: docs/CI-CD/GitHub
sidebar:
  open: true
---

### Connecting to a docker repo with creds
1. `printf "my_username:my_password" | openssl base64 -A` -> dUEHilubgiluBAeiubglIUAEbIUbgaa
2. Create CI/CD variable:
```
$DOCKER_AUTH_CONFIG=
{
  "auths": {
    "registry.example.com:5000": {
      "auth": "dUEHilubgiluBAeiubglIUAEbIUbgaa"
    }
  }
}
```
3. Or if you want to configure it for the runner:
```
[[runners]]
  environment = ["DOCKER_AUTH_CONFIG={\"auths\":{\"registry.example.com:5000\":{\"auth\":\"dUEHilubgiluBAeiubglIUAEbIUbgaa\"}}}"]
```

