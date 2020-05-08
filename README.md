### CI Tools Demo

A __docker-compose__ based environment generator for testing CI/CD tools. :neckbeard:

![Docker CI Tools](screenshots/docker-ci-tools.png)

> WARNING - This solution is not production ready. Use at your own risk.

### Requirements
- Linux (...what else?)
- docker-compose > 1.25

### Getting started

To get all docker containers up and running, in __docker-ci-tool-stack/__ use:

```
- git submodule init
- git submodule update
- docker-compose up -d
```

Go grab a coffee... :coffee:

> INFO - Should you encounter the Docker error “max virtual memory areas vm.max_map_count [65530] is too low” when starting Docker containers, please follow [these guidelines](https://github.com/maxyermayank/docker-compose-elasticsearch-kibana/issues/10#issuecomment-612000396). 

Enable the admin user in Nexus:

```
- docker exec -it docker-ci-tool-stack_nexus_1 cat /nexus-data/admin.password
- Use the password printed above to replace the [admin] user’s password to [admin123]
- Surf to http://localhost:18081
```

Kickoff Jenkins:

```
- Surf to http://localhost:18080
- Login with admin/password
- Trigger the SEED job
```

Congrats, your new CI/CD testing environment is ready! :v:

### Selenium Grid

You have start the selenium grid with a separate command, since the selenium container are
not part of the default docker-compose.yml.

```
docker-compose -f docker-compose-selenium.yml up
```

#### Access Tools

| *Tool* | *Link* | *Credentials* |
| ------------- | ------------- | ------------- |
| Jenkins | http://localhost:18080/ | admin/password |
| SonarQube | http://localhost:19000/ | admin/admin |
| Nexus | http://localhost:18081/ | admin/admin123 |
| GitLab | http://localhost | root/5iveL!fe |
| Selenium Grid | http://localhost:4444/grid/console | no login required |
| Conference App | http://localhost:48080/currentSessions | no login required |

#### Credits (c)

Original version by Marcel Birkner: [marcelbirkner/docker-ci-tool-stack](https://github.com/marcelbirkner/docker-ci-tool-stack).

Article: [Continuous Integration Platform Using Docker Containers: Jenkins, SonarQube, Nexus, GitLab](https://blog.codecentric.de/en/2015/10/continuous-integration-platform-using-docker-container-jenkins-sonarqube-nexus-gitlab)

This version introduced new features like Jenkins JCasC, up to date dependencies, usage of TAGs, etc... as well as a brief kickoff documentation.
