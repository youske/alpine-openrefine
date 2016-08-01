FROM youske/alpine-java:latest
MAINTAINER youske@gmail.com

ENV OPENREFINE_VERSION=2.6-beta.1
ENV TARGET=openrefine-linux-${OPENREFINE_VERSION}
ENV DOWNLOAD=https://github.com/OpenRefine/OpenRefine/releases/download/${OPENREFINE_VERSION}/${TARGET}.tar.gz
ENV WORK_DIR=/mnt.refine

WORKDIR /

# Install Headless JRE after updating installed packages.
RUN apk update --no-cache && apk add wget --no-cache

RUN wget -q --no-check-certificate ${DOWNLOAD} -O- | tar zx && ln -sf  ${TARGET} /openrefine

RUN rm -rf /tmp/*

EXPOSE 3333
RUN mkdir ${WORK_DIR}
ENTRYPOINT ["/init"]
CMD ["/openrefine-2.6-beta.1/refine", "-i", "0.0.0.0", "-d", "${WORK_DIR}"]
