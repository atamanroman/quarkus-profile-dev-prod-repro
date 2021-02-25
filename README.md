# REPRO for [prod/dev profile issue](https://quarkusio.zulipchat.com/#narrow/stream/187030-users/topic/ENVs.20required.20in.20prod.20profile.20break.20dev)

## Steps:

- generate a project from https://code.quarkus.io/ (everything default, commit #1)
- add application.properties with `%prod.quarkus.http.port=${HTTP_PORT}` (commit #2)
- run with `mvn compile quarkus:dev` -> works ✅
- build with `mvn clean install`
- run with `java -jar target/quarkus-app/quarkus-run.jar` -> breaks as expected ✅
- run with `QUARKUS_PROFILE=dev java -jar target/quarkus-app/quarkus-run.jar` -> breaks ❌

```
ra@mbp16:repro master ✗ 2m △ ➜ java -version
openjdk version "11.0.10" 2021-01-19
OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.10+9)
OpenJDK 64-Bit Server VM AdoptOpenJDK (build 11.0.10+9, mixed mode)
```
