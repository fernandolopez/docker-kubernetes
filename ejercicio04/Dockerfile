FROM openjdk:8-jre
COPY passwordapi.jar /

EXPOSE 8080
RUN useradd -U java
USER java:java

CMD java -jar passwordapi.jar