## Dockerfile for a haskell environment
## TAG 7.10-buster
##
FROM       buildpack-deps:buster

## ensure locale is set during build
ENV LANG C.UTF-8

RUN apt-get update && \
    apt-get install -y --no-install-recommends gnupg ca-certificates dirmngr curl git && \
    echo 'deb http://downloads.haskell.org/debian buster main' > /etc/apt/sources.list.d/ghc.list && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA3CBA3FFE22B574 && \
    apt-get update && \
    apt-get install -y --no-install-recommends ghc-7.10.3 cabal-install-3.2 \
        ghc-7.10.3-prof libtinfo-dev && \
    rm -rf "$GNUPGHOME" /var/lib/apt/lists/* /stack.tar.gz

ENV PATH /root/.cabal/bin:/root/.local/bin:/opt/cabal/3.2/bin:/opt/ghc/7.10.3/bin:$PATH

## run ghci by default unless a command is specified
CMD ["ghci"]
