# cas-oauth2-example

#### Впровадження проекту
Це приклад CAS 5, що підтримує підтримку OAuth2.

#### Підготуйте
Залежний проект spring-boot-shiro не випускається в центральний репозиторій Maven, вам потрібно встановити його локально.

```bash
cd cas-server/src/main/resources

keytool -exportcert -alias cas -keystore cas.keystore -storepass 123456 -rfc -file ./cas.cer

keytool -import -v -trustcacerts -alias cas -file cas.cer -keystore $JAVA_HOME/jre/lib/security/cacerts -keypass 123456 -storepass changeit
```

#### Додати hosts
```
127.0.0.1	cas.example.org
```

#### Початок cas-server
 
Реєстрація клієнтської служби реєструється за допомогою JSON, див. Json під cas-server / src / main / resources / services.

`mvn clean package`

`java -jar cas-server/target/cas.war`

Доступ https://cas.example.org:8443

#### Запустіть  cas-client

`mvn clean package spring-boot:run`

Доступ `http://localhost:9000/ping` Перейти до процесу сертифікації CAS OAuth2
Доступ `http://localhost:9000/foo`  Не потрібна сертифікація
Доступ `http://localhost:9000/logout` Вихід 
