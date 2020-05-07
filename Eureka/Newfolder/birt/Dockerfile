FROM openjdk:11-jre-slim
RUN mkdir /app && apt-get update -y
COPY BirtScheduler.jar /app
EXPOSE 8085
CMD ["java", "-jar", "/app/BirtScheduler.jar"]