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
    -DWANT_MONOLITH=ON \
    -DLINUX=ON \
    -DCMAKE_BUILD_TYPE=DEBUG \
    -DCMAKE_C_COMPILER=clang \
    -DCMAKE_CXX_COMPILER=clang++ \
    ..

  make && make install

  cd "${root}"
}

build

