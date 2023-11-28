#使用 Maven 镜像构建项目的镜像：
#优势：
#
#自动化构建： 使用 Maven 构建过程自动化，确保了项目的编译、测试和打包。
#灵活性： 可以使用 Docker 镜像在任何具有 Maven 环境的地方构建项目，不受环境限制。
#镜像轻量化： 构建的镜像相对较小，因为只包含了编译后的输出和运行时所需的内容。
#适用场景：
#
#持续集成/持续交付（CI/CD）： 适用于自动化部署和构建流程，例如在 CI/CD 环境中。
#需要频繁构建： 适用于需要频繁更改和构建的项目，例如开发和测试阶段。


#FROM maven:3.8.1-jdk-8-slim as builder
#WORKDIR /app
#COPY pom.xml .
#COPY src ./src
#RUN mvn package -DskipTests
#CMD ["java","-jar","/app/target/sql-father-backend-0.0.1-SNAPSHOT.jar","--spring.profiles.active=prod"]


# 使用 openjdk:8-jdk-alpine 作为基础镜像，该镜像包含了 OpenJDK 8 和 Alpine Linux
FROM openjdk:8-jdk-slim
# 设置时区为中国上海
ENV TZ=Asia/Shanghai
# 创建一个卷，将宿主机的 /tmp 目录挂载到容器内的 /tmp 目录
WORKDIR /app
# 将本地的 websocket-demo.jar 复制到容器内的 /app 目录
ADD my-sql-backend.jar my-sql-backend.jar
EXPOSE 8102
ENTRYPOINT ["java", "-jar", "-Dserver.port=8102", "-Dspring.profiles.active=prod", "/app/my-sql-backend.jar"]