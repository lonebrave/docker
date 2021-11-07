FROM ubuntu:20.04
LABEL Name=nickhasser/nut Version=0.0.1
RUN apt-get update && apt-get install -y \
    nut-snmp \
    && rm -rf /var/lib/apt/lists/*
CMD ["sh"]