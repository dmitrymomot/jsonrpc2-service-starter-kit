FROM dmitrymomot/healthcheck:alpine
ENV APP_PORT=8080
WORKDIR /
COPY ./rbac_model.conf /
COPY ./rbac_policy.csv /
COPY ./schoolapp-rpc /
EXPOSE $APP_PORT
CMD ["/schoolapp-rpc"]
