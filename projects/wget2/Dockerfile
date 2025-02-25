# Copyright 2016 Google Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
################################################################################

# Using Ubuntu 16.04 because of breakage on Ubuntu 20.04.
# See https://github.com/google/oss-fuzz/issues/6291 for more details.
FROM gcr.io/oss-fuzz-base/base-builder:xenial
# Delete line above and uncomment line below to upgrade to 20.04.
# FROM gcr.io/oss-fuzz-base/base-builder
RUN apt-get update && apt-get install -y \
 make \
 pkg-config \
 gettext \
 autogen \
 autopoint \
 autoconf \
 automake \
 libtool \
 texinfo \
 flex \
 bison \
 gettext \
 gengetopt \
 curl \
 gperf \
 wget \
 python \
 lzip \
 rsync

ENV GNULIB_TOOL $SRC/gnulib/gnulib-tool
RUN git clone git://git.savannah.gnu.org/gnulib.git
RUN git clone --depth=1 --recursive https://git.savannah.gnu.org/git/libunistring.git
RUN git clone --depth=1 --recursive https://gitlab.com/libidn/libidn2.git
RUN git clone --depth=1 --recursive https://github.com/rockdaboot/libpsl.git
RUN git clone --depth=1 https://git.lysator.liu.se/nettle/nettle.git
RUN git clone --depth=1 https://gitlab.com/gnutls/gnutls.git
RUN wget -O- https://ftp.gnu.org/pub/gnu/libmicrohttpd/libmicrohttpd-latest.tar.gz|tar xz

RUN git clone --recursive https://gitlab.com/gnuwget/wget2.git

WORKDIR wget2
COPY build.sh $SRC/
