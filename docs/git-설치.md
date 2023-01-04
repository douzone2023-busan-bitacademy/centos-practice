## git 2.9.5 설치

1. 의존성 라이브러리
   # yum install curl-devel
   # yum install expat-devel
   # yum install gettext-devel
   # yum install openssl-devel
   # yum install zlib-devel
   # yum install perl-devel

2. 다운로드
   # wget https://mirrors.edge.kernel.org/pub/software/scm/git/git-2.9.5.tar.gz

3. 압축 풀기
  # tar xvfz git-2.9.5.tar.gz

4.소스 디렉토리
  # cd git-2.9.5
  # pwd

5. configure
  # ./configure --prefix=/usr/local/douzone2021/git

6. 빌드
  # make all doc html info
   
7. 설치
  # make install install-doc install-html install-info

8. 설정(/etc/profile)
# git
PATH=$PATH:/usr/local/douzone2021/git/bin

9. git 환경 설정

# git config --global user.name "douzone-busan-bitacademy"
# git config --global user.email "douzone.busan.bitacademy@gmail.com"

10. git 사용하기

# mkdir centos-practices
# cd centos-practices
# git init
# git add -A
# git commit -m "first commit"
# git remote add origin https://github.com/douzone-busan-bitacademy/centos-practices.git
# git push -u origin master

================
# git add -A
# git commit -m "...."
# git push 


=========================================================


# git clone https://github.com/douzone-busan-bitacademy/javastudy.git
# cd javastudy
# mvn clean package










  






