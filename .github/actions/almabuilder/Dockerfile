FROM almalinux/9-base

RUN dnf config-manager --enable crb && yum update -y
RUN yum install -y g++ cmake make {libarchive,bzip2,zlib,sqlite,curl,libunistring,pcre2}-devel
RUN stat /work/src && stat /work/build
RUN cmake -B /work/build -S /work/src -DCMAKE_BUILD_TYPE=Release -DLNAV_USE_VCPKG=OFF -DLNAV_USE_CARGO=OFF
RUN make -C /work/build -j $(($(nproc)<4 ? $(nproc) : 4))
