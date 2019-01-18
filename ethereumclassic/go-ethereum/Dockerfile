ARG GETH_VERSION

FROM golang:1.10.2

ENV PATH=/usr/lib/go-1.10.2/bin:$PATH

RUN \
  apt-get update && apt-get upgrade -q -y && \
  apt-get install -y --no-install-recommends git make gcc libc-dev ca-certificates && \
  curl https://sh.rustup.rs -sSf | sh && \
  go get -d github.com/ethereumclassic/go-ethereum/... && \
  cd "$GOPATH/src/github.com/ethereumclassic/go-ethereum" && \
  make cmd/geth && \
  cd - && \
  mv "$GOPATH/src/githbu.com/ethereumclassic/go-ethereum/bin/geth" ./bin/

RUN ln -s ./bin/geth geth

# Utilities
RUN apt-get install -y curl

EXPOSE 8545 8546 30303 30303/udp

ENTRYPOINT ["./geth"]
