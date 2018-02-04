#!/usr/bin/env bash

set -e

root=$(pwd)
input="${root}/INPUT"
output="${root}/OUTPUT"
build="${root}/BUILD"

component=$1
config=$2

fail() {
  echo $1 >&2 && exit 1
}

build() {
  mkdir -p "${build}"  
  cd "${build}"
  
  cmake \
    -DCMAKE_INSTALL_PREFIX="${output}" \
    -DSHARED=NO \
    -DWANT_MONOLITH=ON \
    -DCMAKE_BUILD_TYPE=RELEASE \
    -DCMAKE_C_COMPILER=clang \
    -DWANT_DEMO=OFF \
    ..

  make && make install

  cd "${root}"
}

build

