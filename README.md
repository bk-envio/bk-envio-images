## Buildkite Envio Docker Images



This project contains pre-built Docker Images for Buildkite to perform build tasks as fast as possible. Currently, it is derivered from Amazon's CodeBuild Repository thsat is adapted for Buildkite environment.



## How to use with `docker-compose`



Assume you have `docker-compose.yml` in `.buildkite/`

```
version: '3.8'

services:
  app:
    image: 'bkenvio/ubuntu:latest'
    working_dir: /app
    volumes:
      - $PWD:/app
      - /disk2/caches:/app/.cache
```

To use individually use buildkite docker plugin.

```
steps:
  - command: yarn --version
    plugins:
      - docker#v3.5.0:
          image: "bkenvio/ubuntu:latest"
```



## Version management



You can use `goenv`, `rbenv`, `phpenv` and `n` (for node-js) to install specific version. We already included latest available versions. See below table for pre-installed tools

| **Tool**    | **Installed Version** | **Manager** |
| ----------- | --------------------- | ----------- |
| corretto:8  | 1.8.0_232             | -           |
| corretto:11 | 11.0.5                | -           |
| dotnet:3.1  | 3.1.103               | -           |
| php:7.4     | 7.4.1                 | `phpenv`    |
| php:7.3     | 7.3.13                | `phpenv`    |
| ruby:2.7    | 2.7.1                 | `rbenv`     |
| ruby:2.6    | 2.6.6                 | `rbenv`     |
| node:14     | 14.3.0                | `n`         |
| node:12     | 12.17.0               | `n`         |
| python:3.8  | 3.8.1                 | `pyenv`     |
| python:3.7  | 3.7.6                 | `pyenv`     |
| golang1.12  | 1.12.17               | `goenv`     |
| golang1.13  | 1.13.8                | `goenv`     |
| golang1.14  | 1.14.3                | `goenv`     |



Also all required libs and tools installed below but not limited to:



| **Tool/Lib**             |
| ------------------------ |
| powershell               |
| nuget                    |
| kubectl                  |
| aws-iam-authenticator    |
| pip                      |
| yarn                     |
| bundler                  |
| java                     |
| gradle                   |
| maven                    |
| android-sdk              |
| google-chrome-stable     |
| firefox-stable           |
| buildkite-agent          |
| stunnel                  |
| jq                       |
| postgresql-12-server-dev |
| postgresql-12-client     |
| bison                    |
| sqlite                   |
| yaml                     |
| json                     |
| imagemagick              |
| libvips                  |
| libmaxminddb             |
| libgit2                  |

... and many more. See `Dockerfile` for more.



Please note that, Docker (inline) has been removed. You can always attach your host's docker using compose or volume.



(C) 2020 Portions Gencer W. Genç

(C) 2020 Based on AWS Code Build.

Licensed as **MIT**. Also see Amazon Software License which is attached to this repository.

