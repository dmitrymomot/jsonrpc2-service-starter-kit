FROM alpine:latest
RUN apk add --update ca-certificates && \
    rm -rf /var/cache/apk/* /tmp/*
ENV APP_PORT=8080
WORKDIR /
COPY k8s/prod/ca-certificate.crt /
COPY schoolapp-api /
EXPOSE $APP_PORT
CMD ["/schoolapp-api"]
