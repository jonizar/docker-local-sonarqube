# docker-local-sonarqube

1. Clone this project
2. install **docker** and **docker compose**
3. install **Sonar-Scanner CLI**
4. install **docker dekstop**
5. run docker dekstop
6. run this command :
  ```
docker network create my-bridge-network
  ```
7. check network
   ```
   docker network ls
   ```
8. run this command to start container
  ```
  docker-compose -f postgresql.yaml up -d
  docker-compose -f sonarqube.yaml up -d
  ```
9. create database in postgresql
10. open browser http://localhost:9002 input default password **admin/admin**

to scan project, use sonar-scanner then create token, follow this step: login → Administration → Security → Users → create user or use user existing → click in row token to generate token.

run this command to scan in project directory

for java project
```
sonar-scanner -Dsonar.projectKey="AMAN_notification-service" -Dsonar.sources=src/main -Dsonar.java.binaries=. \
 -Dsonar.host.url=http://localhost:9002 -Dsonar.login=abcdtoken \
 -Dsonar.sourceEncoding=UTF-8 \
 -Dsonar.exclusions='src/main/webapp/content/**/*.*, src/main/webapp/i18n/*.js, target/classes/META-INF/resources**/*.*
```

for php project
```
sonar-scanner.bat -Dsonar.projectKey=TEST_service" -Dsonar.host.url=http://localhost:9002 -Dsonar.token=tokenthatyoucreated -Dsonar.sourceEncoding=UTF-8 -Dsonar.exclusions='**/*.java'
```
   
