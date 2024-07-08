FROM texlive/texlive:latest

ARG UNAME
ARG UID
ARG GID

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    build-essential \
    git \
    cpanminus && \
    apt-get clean && \
    apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/*

RUN cpanm -n \
	YAML::Tiny \
	File::HomeDir \
	Unicode::GCString

RUN tlmgr update --self && \
    tlmgr install latexindent

RUN useradd --shell /bin/bash --uid $UID --non-unique --create-home $UNAME
RUN groupmod --gid $GID --non-unique $UNAME
