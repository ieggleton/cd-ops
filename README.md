# Env Deploy

This is unlikely to be useful outside of the organisation for which it was designed

## Deploy and (Optionally) Test Microservices to k8s using kustomize

* [`TBD`](https://www.idonotexistyet.com) 

## Pre Reqs

## Usage

### Trigger test functionality

NB: Only available functionality at this stage

Trigger a test repo, specified by a project-slug to run a set of tests with:
- A set of cucumber tags to run
- An image to be deployed
- The Git branch on which tests run

As this uses the CircleCI API it will require a token to be setup and assigned to an environment
variable `$CIRCLECI_API_TOKEN`

#### example.yml

```yml
version: 2.1
      orbs:
        packagecloud: ieggleton/env-deploy@x.y.z
      jobs:
        build:
          docker:
          - image: circleci/node:10.16.3
          steps:
            - checkout

            - run:
                name: Repo build and Test
                command: |
                  commands

            - run:
                name: Image Deploy 
                command: |
                  my deploy commands

            - env-deploy/run-tests
                project-slug: vcs/org-name/my-test-repo
                image-tag: my-deployable:0.0.0
                test-tags: "not @ignore"
                test-branch: develop
```
