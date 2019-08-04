SH:RethinkDB:
RethinkDB Build Instructions
Here are some instructions to build RethinkDB from a minimal-ish install (server or minimal) on various platforms. Should work for branches v2.3.x, v2.4.x, and next. (Follow the `./configure` line with `make -j8` to actually build.)

These instructions include likely unnecessary dependencies such as mg, git, and epel-release. I did install them on the VM, and I didn't test whether things worked without installing them.

These instructions might fail to work if you have the wrong version of a dependency already on your system. You can use --fetch to work around this. For example, if see a build error talking about Node.JS, you might need to pass --fetch npm to ./configure. Run ./configure --help for a list of options.

These instructions might not work for RethinkDB 2.3.6 source tarballs. The releases v2.3.6.srh.1 and v2.3.6.srh.2 contain additional fixes for newer platforms. They also have prebuilt unsigned packages. See the srh releases page for the latest releases.

bionic
apt install build-essential protobuf-compiler python \
    libprotobuf-dev libcurl4-openssl-dev libboost-all-dev \
    libncurses5-dev libjemalloc-dev wget m4 clang libssl-dev
./configure --allow-fetch CXX=clang++
make -j8

# to build a .deb package:
apt install debhelper
make build-deb UBUNTU_RELEASE=bionic
artful
apt install mg
apt install build-essential protobuf-compiler python \
    libprotobuf-dev libcurl4-openssl-dev libboost-all-dev \
    libncurses5-dev libjemalloc-dev wget m4 clang libssl-dev
./configure --allow-fetch CXX=clang++
zesty
apt install mg
apt install build-essential protobuf-compiler python \
    libprotobuf-dev libcurl4-openssl-dev libboost-all-dev \
    libncurses5-dev libjemalloc-dev wget m4 clang libssl1.0-dev
./configure --allow-fetch CXX=clang++
xenial
apt install mg
apt-get install build-essential protobuf-compiler python \
    libprotobuf-dev libcurl4-openssl-dev libboost-all-dev \
    libncurses5-dev libjemalloc-dev wget m4 g++ libssl-dev
./configure --allow-fetch
trusty
apt install mg
apt-get install build-essential protobuf-compiler python \
    libprotobuf-dev libcurl4-openssl-dev libboost-all-dev \
    libncurses5-dev libjemalloc-dev wget m4 g++
./configure --allow-fetch
centos7
yum install mg git
yum install epel-release  # probably not necessary
yum update
yum install openssl-devel libcurl-devel wget tar m4 \
    git-core boost-static m4 gcc-c++ npm ncurses-devel \
    which make ncurses-static zlib-devel zlib-static \
    protobuf-devel protobuf-static jemalloc-devel
yum install bzip2 patch
./configure --allow-fetch
jessie
apt install sudo mg git
apt install build-essential protobuf-compiler python \
    libprotobuf-dev libcurl4-openssl-dev libboost-all-dev \
    libncurses5-dev libjemalloc-dev wget m4 g++ libssl-dev
./configure --allow-fetch
stretch
apt install sudo mg git
apt install build-essential protobuf-compiler python \
    libprotobuf-dev libcurl4-openssl-dev libboost-all-dev \
    libncurses5-dev libjemalloc-dev wget m4 clang libssl1.0-dev
./configure --allow-fetch CXX=clang++
buster
apt install git
apt install build-essential protobuf-compiler python \
    libprotobuf-dev libcurl4-openssl-dev libboost-all-dev \
    libncurses5-dev wget m4 clang libssl-dev
./configure --allow-fetch CXX=clang++

# to build a .deb package:
apt install debhelper curl
make build-deb DEB_RELEASE=buster
END OF PAGE
