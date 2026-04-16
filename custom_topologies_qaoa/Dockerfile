FROM --platform=linux/amd64 python:3.9-slim-bookworm

WORKDIR /app

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
       git \
       build-essential \
       gfortran \
       libopenblas-dev \
       liblapack-dev \
       pkg-config \
    && rm -rf /var/lib/apt/lists/*

RUN python -m pip install --upgrade pip wheel "setuptools<82"

COPY requirements.txt /app/requirements.txt
RUN python -m pip install --no-build-isolation "numpy==1.19.5"
RUN python -m pip install --no-build-isolation -r /app/requirements.txt

RUN git clone https://github.com/quantumdoubleblind/qsw_2023.git

COPY run.sh /app/run.sh
RUN chmod +x /app/run.sh

CMD ["/bin/sh", "/app/run.sh"]
