# Build Stage
FROM ubuntu as builder

## Install build dependencies.
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y build-essential pkg-config libffi-dev
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y clang llvm

COPY . /repo
WORKDIR /repo/fuzz
RUN make fuzz-execute-from-string

FROM ubuntu
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y libffi-dev
COPY --from=builder /repo/fuzz/fuzz-execute-from-string /fuzz-execute-from-string