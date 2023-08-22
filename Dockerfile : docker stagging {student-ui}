FROM openjdk:8 as builder
RUN apt-get update -y && apt-get install maven -y
WORKDIR /mnt
COPY student-ui /mnt/student-ui
WORKDIR /mnt/student-ui
RUN mvn package

FROM tomcat
RUN rm -rvf /usr/local/tomcat/webapps
RUN mv /usr/local/tomcat/webapps.dist /usr/local/tomcat/webapps
COPY --from=builder /mnt/student-ui/target/*.war /usr/local/tomcat/webapps
CMD /usr/local/tomcat/bin/startup.sh; sleep inf
