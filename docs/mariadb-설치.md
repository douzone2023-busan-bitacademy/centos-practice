## MariaDB 설치

0. 작업 디렉토리 확인
```bash
# pwd
/root
```

1. 의존 라이브러리 설치
```bash
# yum install -y gcc
# yum install -y gcc-c++
# yum install -y libtermcap-devel
# yum install -y gdbm-devel
# yum install -y zlib*
# yum install -y libxml*
# yum install -y freetype*
# yum install -y libpng* 
# yum install -y flex
# yum install -y gmp
# yum install -y ncurses-devel
# yum install -y cmake.x86_64
# yum install -y libaio
```
iconv 소스 컴파일 설치를 한다.
```bash
# wget --no-check-certificate https://ftp.gnu.org/pub/gnu/libiconv/libiconv-1.17.tar.gz
# tar xvfz libiconv-1.17.tar.gz
# cd libiconv-1.17
# ./configure --prefix=/usr/local
# make
# make install
```

2. 소스 다운로드
```bash
# wget https://downloads.mariadb.org/interstitial/mariadb-10.1.48/source/mariadb-10.1.48.tar.gz 
```

3. 압축 풀기
```bash
# tar xvfz mariadb-10.1.48.tar.gz
```

4. 소스 디렉토리 이동
```bash
# cd mariadb-10.1.48
```

5. 빌드 환경 설정 
```bash
# cmake -DCMAKE_INSTALL_PREFIX=/usr/local/douzone2023/mariadb -DMYSQL_USER=mysql -DMYSQL_TCP_PORT=3307 -DMYSQL_DATADIR=/usr/local/douzone2023/mariadb/data -DMYSQL_UNIX_ADDR=/usr/local/douzone2023/mariadb/tmp/mariadb.sock -DINSTALL_SYSCONFDIR=/usr/local/douzone2023/mariadb/etc -DINSTALL_SYSCONF2DIR=/usr/local/douzone2023/mariadb/etc/my.cnf.d -DDEFAULT_CHARSET=utf8 -DDEFAULT_COLLATION=utf8_general_ci -DWITH_EXTRA_CHARSETS=all -DWITH_ARIA_STORAGE_ENGINE=1 -DWITH_XTRADB_STORAGE_ENGINE=1 -DWITH_ARCHIVE_STORAGE_ENGINE=1 -DWITH_INNOBASE_STORAGE_ENGINE=1 -DWITH_PARTITION_STORAGE_ENGINE=1 -DWITH_BLACKHOLE_STORAGE_ENGINE=1 -DWITH_FEDERATEDX_STORAGE_ENGINE=1 -DWITH_PERFSCHEMA_STORAGE_ENGINE=1 -DWITH_READLINE=1 -DWITH_SSL=bundled -DWITH_ZLIB=system
```

6. 빌드
```bash
# make
```

7. 설치
```bash
# make install
```
8. 설정 작업을 위해 root 홈디렉토리 이동
```bash
# cd 
# pwd
/root
```

9. 계정 생성
```bash
# groupadd mysql
# useradd -M -g mysql mysql 
```

10. mariadb 인스톨 디렉토리 소유자 변경
```bash
# chown -R mysql:mysql /usr/local/douzone2023/mariadb
```

10. 설정파일 위치 변경
```bash
cp -R /usr/local/douzone2023/mariadb/etc/my.cnf.d /etc
```

11. 기본(관리) 데이터베이스(mysql) 생성
```bash
# /usr/local/douzone2023/mariadb/scripts/mysql_install_db --user=mysql --basedir=/usr/local/douzone2023/mariadb --defaults-file=/usr/local/douzone2023/mariadb/etc/my.cnf --datadir=/usr/local/douzone2023/mariadb/data
```
12. 서버 구동
```bash
# /usr/local/douzone2023/mariadb/bin/mysqld_safe &
```

13. root 패스워드 설정
```bash
# /usr/local/douzone2023/mariadb/bin/mysqladmin -u root password '........'
```

14. 데이터베이스 접속 테스트
```bash
# /usr/local/douzone2023/mariadb/bin/mysql -u root -p
```

15. path 설정(/etc/profile)
```bash
# mysql
export PATH=$PATH:/usr/local/douzone2023/mariadb/bin
```

16. 서비스(데몬, Daemon) 등록/시작/중지
```bash
# cp /usr/local/douzone2023/mariadb/support-files/mysql.server /etc/init.d/mariadb
# systemctl enable mariadb
# ps -ef | grep mysql
root       865     1  0 16:23 ?        00:00:00 /bin/sh /usr/local/douzone2023/mariadb/bin/mysqld_safe --datadir=/usr/local/douzone2023/mariadb/data --pid-file=/usr/local/douzone2023/mariadb/data/lx.kickscar.me.pid
mysql      968   865  0 16:23 ?        00:00:00 /usr/local/douzone2023/mariadb/bin/mysqld --basedir=/usr/local/douzone2023/mariadb --datadir=/usr/local/douzone2023/mariadb/data --plugin-dir=/usr/local/douzone2023/mariadb/lib/plugin --user=mysql --log-error=/usr/local/douzone2023/mariadb/data/lx.kickscar.me.err --pid-file=/usr/local/douzone2023/mariadb/data/lx.kickscar.me.pid
# kill -9 865 968
# systemctl start mariadb
# ps -ef | grep mysql
```

17. 재부팅 후, mysql 클라이언트로 접속 테스트
```sh
# mysql -u root -p
password:
MariaDB [(none)]>
```
