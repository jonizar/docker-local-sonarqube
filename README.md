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
9. koneksikan postgres dan buat database
10. buka browser http://localhost:9002 masukan password default admin/admin

untuk scan project kita pakai sonar-scanner yang telah di install lalu buat token terlebih dahulu dengan cara: login → Administration → Security → Users → create user atau pakai user existing → klik di row token untuk generate token

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
   
