# New topics

## How to be possible for a user with only docker, be able to run the application without having to install the rest of the dependencies?

```dockerfile
FROM eclipse-temurin:21-jdk-apline

RUN apk add unzip && \
    mkdir -p /build/app/bin && \
    mkdir -p /build/app/src

WORKDIR /build
ADD https://github.com/JetBrains/kotlin/releases/download/v1.9.21/kotlin-compiler-1.9.21.zip .

RUN unzip kotlin-compiler-1.9.21.zip -d /opt

WORKDIR /build/app/src
COPY src/ ./

RUN /opt/kotlinc/bin/kotlinc Hello.kt -include-runtime -d ../bin/Hello.jar  

WORKDIR /opt/isel/tvs/hello
RUN cp /build/app/bin/Hello.jar .

CMD ["java", "-jar", "Hello.jar"]
```
