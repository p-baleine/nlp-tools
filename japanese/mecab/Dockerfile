FROM alpine:3.11.6

ENV MECAB_URL='https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7cENtOXlicTFaRUE'
ENV MECAB_IPADIC_URL='https://drive.google.com/uc?export=download&id=0B4y35FiV1wh7MWVlSDBCSXZMTXM'

WORKDIR /opt

RUN apk add --no-cache make gcc g++ \
# mecab
  && wget -O mecab-0.996.tar.gz $MECAB_URL \
  && tar zxvf mecab-0.996.tar.gz \
  && cd mecab-0.996 \
  && ./configure \
  && make \
  && make install \
# mecab ipadic
  && cd /opt \
  && wget -O mecab-ipadic-2.7.0-20070801.tar.gz $MECAB_IPADIC_URL \
  && tar zxvf mecab-ipadic-2.7.0-20070801.tar.gz \
  && cd mecab-ipadic-2.7.0-20070801 \
  && ./configure  --with-charset=utf8 \
  && make \
  && make install \
# for helper scripts
  && mkdir mecab-scripts

COPY scripts/analyze /opt/mecab-scripts/analyze

RUN chmod +x /opt/mecab-scripts/analyze \
  && echo 'PATH=${PATH}:/opt/mecab-scripts' > /etc/profile.d/mecab.sh
