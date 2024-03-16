###########################################
# BASE IMAGE
###########################################

FROM ubuntu AS build

COPY requirements.txt ./

RUN apt-get update && \apt-get install -y python3 python3-pip &&\ pip install -r requirements.txt 

COPY . .

ENTRYPOINT ["/app"]

############################################
# HERE STARTS THE MAGIC OF MULTI STAGE BUILD
############################################

FROM python:3-slim AS build-env
COPY . /app
WORKDIR /app

FROM gcr.io/distroless/python3
COPY --from=build-env /app /app
WORKDIR /app
CMD ["hello.py", "/etc"]
