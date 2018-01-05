FROM airdock/oracle-jdk:jdk-1.8

COPY ./crt/nginx.crt /opt/

RUN apt-get update && \
    apt-get install -y zip wget vim && \
    wget -P /opt https://s3-us-west-2.amazonaws.com/wso2-stratos/wso2am-2.0.0.zip && \
    apt-get clean && \
    unzip /opt/wso2am-2.0.0.zip -d /opt && \
    rm /opt/wso2am-2.0.0.zip && \
    keytool -import -file /opt/nginx.crt -keystore /opt/wso2am-2.0.0/repository/resources/security/client-truststore.jks -storepass wso2carbon -alias wso2carbon2 -noprompt && \
    rm /opt/nginx.crt

EXPOSE 9443 8243 8280 9763
WORKDIR /opt/wso2am-2.0.0
CMD ["bin/wso2server.sh"]
