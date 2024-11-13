## Run via cloud-init

- Go to GitLab group > "Build" > "Runners" > "Create runner" to [create a group runner](<https://docs.gitlab.com/ee/ci/runners/runners_scope.html#create-a-group-runner-with-a-runner-authentication-token>)
  - (or go to GitLab project > "Settings" > "CI/CD" > "Runners" > "New project runner" to [create a project runner](<https://docs.gitlab.com/ee/ci/runners/runners_scope.html#create-a-project-runner-with-a-runner-authentication-token>))
- Append the command displayed in "Step 1" (`gitlab-runner register ...`) to `sh -xs --`:

```
#!/bin/sh
curl -fL https://github.com/rafaelgieschke/gitlab-runner/raw/main/user-data | sh -xs -- 
```

If you want jobs to be able to use [Docker-in-Docker](https://docs.gitlab.com/ee/ci/docker/using_docker_build.html#docker-in-docker-with-tls-enabled-in-the-docker-executor) (which is insecure!), you have to append additional arguments:

```
--docker-privileged --docker-volumes /certs/client
```
