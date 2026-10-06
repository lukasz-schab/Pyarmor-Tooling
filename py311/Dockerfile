FROM debian:12@sha256:f37a335e82bca302e955fa39f9dfe28f1be618f016f8a2b56318e5a5111afc26

RUN apt-get update && apt-get install -y build-essential gdb lcov pkg-config \
        libbz2-dev libffi-dev libgdbm-dev libgdbm-compat-dev liblzma-dev \
        libncurses5-dev libreadline6-dev libsqlite3-dev libssl-dev \
        lzma lzma-dev tk-dev uuid-dev zlib1g-dev git python3

ADD armor-marshal-311.patch /armor-marshal-311.patch

RUN git clone --depth 1 --branch 3.11 https://github.com/python/cpython.git && \
    cd cpython && \
    patch -p1 -i ../armor-marshal-311.patch && \
    ./configure && \
    make regen-all

ENTRYPOINT [ "/cpython/python" ]
