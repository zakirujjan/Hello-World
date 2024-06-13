# Use the official Maven image to build the application
FROM maven:3.8.4-openjdk-17 AS build
COPY src /home/app/src
COPY pom.xml /home/app
RUN mvn -f /home/app/pom.xml clean package

# Use the official OpenJDK image to run the application
FROM openjdk:17-jdk-slim
COPY --from=build /home/app/target/hello-world-1.0-SNAPSHOT.jar /usr/local/lib/hello-world.jar
ENTRYPOINT ["java", "-jar", "/usr/local/lib/hello-world.jar"]

