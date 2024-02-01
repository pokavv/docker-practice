# 도커 연습
### 가정
- Docker 와 Docker Desktop 설치
- Java, Springboot 세팅
### 개발환경
- JAVA (JDK 17)
- Springboot 3.2.2
- Intellij
### 실습
***2024 02 01***
1. 스프링부트 프로젝트 생성 : [Spring Initializr](https://start.spring.io/)
2. Intellij 우측 Gradle 탭 -> Tasks -> bootJar : build/libs 에 스냅샷 jar 생성 확인
3. build/libs 에 Dockerfile 작성 (Docker 파일엔 확장자 x)
```Dockerfile
FROM openjdk:17
ARG JAR_FILE=*.jar
COPY ${JAR_FILE} app.jar
EXPOSE [포트번호]
ENTRYPOINT ["java","-jar","app.jar"]
```
4. build/libs 폴더에서 터미널 열어 도커에 이미지 업로드
```cmd
docker build -t [설정할 이미지 이름] ./
```
5. 컨테이너로 run 서버
```cmd
docekr run -d -p [포트번호]:[포트번호] [설정한 이미지 이름]
```
6. docker desktop 의 Container 탭에서 서버가 정상적으로 실행되는지 확인
