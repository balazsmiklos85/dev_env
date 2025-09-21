FROM opensuse/leap:15.6

RUN zypper refresh
RUN zypper --non-interactive install --no-recommends \
    texlive-latex
RUN zypper --non-interactive install --no-recommends \
    texlive-babel-english \
    texlive-enumitem \
    texlive-fira \
    texlive-fontawesome \
    texlive-geometry \
    texlive-microtype
RUN zypper clean --all
