FROM alpine:3.11.6

ENV JUMAN_VERSION="7.01"
ENV JUMAN_FILE="juman-${JUMAN_VERSION}.tar.bz2"
ENV JUMAN_URL="http://nlp.ist.i.kyoto-u.ac.jp/DLcounter/lime.cgi?down=http://nlp.ist.i.kyoto-u.ac.jp/nl-resource/juman/${JUMAN_FILE}&name=${JUMAN_FILE}"
ENV KNP_VERSION="4.20"
ENV KNP_FILE="knp-${KNP_VERSION}.tar.bz2"
ENV KNP_URL="http://nlp.ist.i.kyoto-u.ac.jp/DLcounter/lime.cgi?down=http://nlp.ist.i.kyoto-u.ac.jp/nl-resource/knp/${KNP_FILE}&name=${KNP_FILE}"

WORKDIR /opt

RUN apk add --no-cache make gcc g++ zlib-dev \
# Install juman
  && wget -O $JUMAN_FILE $JUMAN_URL \
  && tar jxvf $JUMAN_FILE \
  && cd juman-${JUMAN_VERSION} \
  && ./configure \
  && make \
  && make install \
# Install knp
  && cd /opt \
  && wget -O $KNP_FILE $KNP_URL \
  && tar jxvf $KNP_FILE \
  && cd knp-${KNP_VERSION} \
  && ./configure \
  && make \
  && make install \
# Clean up
  && cd /opt \
  && rm $JUMAN_FILE $KNP_FILE
