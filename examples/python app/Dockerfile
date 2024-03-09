###########################################
# BASE IMAGE
###########################################

FROM ubuntu AS build

COPY requirements.txt ./

RUN apt-get update && \apt-get install -y python3 python3-pip &&\ pip install -r requirements.txt 

COPY . .

ENTRYPOINT ["/app"]

