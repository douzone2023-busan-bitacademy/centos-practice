## Maven 3.8 설치

1. 다운로드
```sh
# wget https://dlcdn.apache.org/maven/maven-3/3.8.7/binaries/apache-maven-3.8.7-bin.tar.gz
```   

2. 압축 풀기
```sh
# tar xvfz apache-maven-3.8.7-bin.tar.gz
```   
   
3. 설치
```sh
# mv apache-maven-3.8.7 /usr/local/douzone2023/maven3.8
```

4. 설정(/etc/profile)
```sh
# maven
export PATH=$PATH:/usr/local/douzone2023/maven3.8/bin
```

5. 확인
```sh
# source /etc/profile
# mvn --version
Apache Maven 3.8.7 (b89d5959fcde851dcb1c8946a785a163f14e1e29)
Maven home: /usr/local/douzone2023/maven3.8
Java version: 17.0.5, vendor: Oracle Corporation, runtime: /usr/local/douzone2023/jdk-17.0.5
Default locale: ko_KR, platform encoding: UTF-8
OS name: "linux", version: "3.10.0-1160.81.1.el7.x86_64", arch: "amd64", family: "unix"
```

