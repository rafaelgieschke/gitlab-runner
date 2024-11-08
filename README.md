## Run via cloud-init

- Follow <https://docs.gitlab.com/ee/ci/runners/runners_scope.html#create-a-group-runner-with-a-runner-authentication-token>
  - or <https://docs.gitlab.com/ee/ci/runners/runners_scope.html#create-a-project-runner-with-a-runner-authentication-token>
- Click "Create runner"
- Append the command displayed in "Step 1" (`gitlab-runner register ...`) to `sh -xs --`:

```
#!/bin/sh
curl -fL https://github.com/rafaelgieschke/gitlab-runner/raw/docker-in-docker/user-data | sh -xs -- 
```
