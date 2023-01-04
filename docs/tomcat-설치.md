## Tomcat9 설치


1. tomcat9 다운로드
```sh
# wget --no-check-certificate https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.70/bin/apache-tomcat-9.0.70.tar.gz
```

2. 압축 풀기
```sh
# tar xvfz apache-tomcat-9.0.70.tar.gz
```

3. 설치
```sh
# mv apache-tomcat-9.0.70 /usr/local/douzone2023/tomcat-9.0.70
# ln -s /usr/local/douzone2021/tomcat-9.0.70 /usr/local/douzone2021/tomcat
```

4. 포트 확인(/usr/local/douzone2021/tomcat/conf/server.xml)
```xml

...

 <Connector port="8080" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />

...

```

5. 실행
```sh
# /usr/local/douzone2023/tomcat/bin/catalina.sh start
# ps -ef | grep tomcat
```

6. 브라우저로 접근 하기
   http://설치서버:8080

7. 중지
```sh
# /usr/local/douzone2023/tomcat/bin/catalina.sh stop
```

9. 서비스 등록 하기
   - [/usr/lib/systemd/system/tomcat.service](https://github.com/douzone2023-busan-bitacademy/centos-practice/blob/main/lx/usr/lib/systemd/system/tomcat.service) 생성
   - 서비스 등록
     ```sh
     # systemctl enable tomcat
     ```
10. tomcat 서비스 실행/중지/재실행
```sh
# systemctl start tomcat
# systemctl stop tomcat
# systemctl restart tomcat
```

11. tomcat manager 설정
   - [/usr/local/douzone2021/tomcat/conf/tomcat-users.xml](https://github.com/douzone2023-busan-bitacademy/centos-practice/blob/main/lx/usr/local/douzone2023/tomcat-9.0.70/conf/tomcat-users.xml) 설정
   - [/usr/local/douzone2021/tomcat/webapps/manager/META-INF/context.xml](https://github.com/douzone2023-busan-bitacademy/centos-practice/blob/main/lx/usr/local/douzone2023/tomcat-9.0.70/webapps/manager/META-INF/context.xml) 설정

12. tomcat 재시작
```sh
    # systemctl stop tomcat
    # ps -ef | grep tomcat
    # systemctl start tomcat
```

13. http://설치서버/manager 접근/인증 하기








 
 

    
