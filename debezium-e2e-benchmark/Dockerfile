FROM centos:8

RUN curl -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-8.repo&&yum makecache
RUN dnf -y install java-11-openjdk java-11-openjdk-devel
RUN dnf -y install python3
RUN dnf -y install gcc gcc-c++  python3-devel python3-requests
RUN python3 -m pip install JPype1==0.6.3
RUN python3 -m pip install JayDeBeApi matplotlib kafka-python scipy

RUN useradd -ms /bin/bash tpc

USER tpc
WORKDIR /home/tpc

RUN mkdir /home/tpc/jdbcdriver
run curl https://repo1.maven.org/maven2/com/ibm/db2/jcc/11.5.6.0/jcc-11.5.6.0.jar --output /home/tpc/jdbcdriver/jcc.jar
run curl https://repo1.maven.org/maven2/mysql/mysql-connector-java/8.0.26/mysql-connector-java-8.0.26.jar --output /home/tpc/jdbcdriver/mysql.jar
run curl https://repo1.maven.org/maven2/com/microsoft/sqlserver/mssql-jdbc/9.4.0.jre11/mssql-jdbc-9.4.0.jre11.jar --output /home/tpc/jdbcdriver/mssql.jar
run curl https://repo1.maven.org/maven2/postgresql/postgresql/9.1-901.jdbc4/postgresql-9.1-901.jdbc4.jar --output /home/tpc/jdbcdriver/postgresql.jar
run curl https://repo1.maven.org/maven2/com/oracle/ojdbc/ojdbc10/19.3.0.0/ojdbc10-19.3.0.0.jar  --output /home/tpc/jdbcdriver/ojdbc10.jar

ADD py/ /home/tpc

CMD ["/usr/bin/tail","-f","/dev/null"]
