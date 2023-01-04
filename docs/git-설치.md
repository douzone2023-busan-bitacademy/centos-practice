## git 2.9.5 설치

1. 의존성 라이브러리
```sh   
# yum -y install curl-devel
# yum -y install expat-devel
# yum -y install gettext-devel
# yum -y install openssl-devel
# yum -y install zlib-devel
# yum -y install perl-devel
```

2. 다운로드
```sh   
# wget --no-check-certificate https://mirrors.edge.kernel.org/pub/software/scm/git/git-2.9.5.tar.gz
```

3. 압축 풀기
```sh   
# tar xvfz git-2.9.5.tar.gz
```

4.소스 디렉토리
```sh   
# cd git-2.9.5
# pwd
```

5. configure
```sh
# ./configure --prefix=/usr/local/douzone2023/git
```

6. 빌드
```sh
  # make all
```

7. 설치
```sh
  # make install
```

8. 설정(/etc/profile)
```sh
# git
export PATH=$PATH:/usr/local/douzone2023/git/bin
```

9. git 설치 확인
```sh
# source /etc/profile
# git --version
# git version 2.9.5
```
만약, 버전이 2.9.5  보다 낮은 경우
```sh
# whereis git
# cd /usr/bin
# rm -f git
# ln -s /usr/local/douzone2023/git/bin/git git
```

10. git 사용하기
```sh
# git clone https://github.com/douzone2023-busan-bitacademy/java-study.git
# cd java-study
# mvn clean package
```










  






