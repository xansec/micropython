# Build Stage
FROM --platform=linux/amd64 ubuntu:20.04 as builder

## Install build dependencies.
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y build-essential pkg-config libffi-dev git python3
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y clang lld


COPY . /repo
WORKDIR /repo
RUN make -j8 CC=clang CXX=clang++

FROM ubuntu:20.04 as package
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y libffi-dev
COPY --from=builder /repo/ports/unix/micropython /fuzz_qstr_compute_hash