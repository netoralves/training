FROM registry.redhat.io/rhel8/go-toolset:latest

ENV QUOTES_VERSION=2.1 \
    SUMMARY="Famous Apps" \
    DESCRIPTION="Famous Quotes is a PoC application for Go and MySQL"

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Quotes 2.1" \
      io.openshift.expose-services="8000:quotes" \
      io.openshift.tags="poc,mysql,golang" \
      name="netoralves/famous-app" \
      version="2.1" \
      usage="podman run -d -e DATABASE_USER=user -e DATABASE_PASSWORD=pass -e DATABASE_NAME=famousdb -p 8000:8000 https://quay.io/repository/netoralves/famous-app"

EXPOSE 8000

COPY . .

RUN go mod init example.com/main && \
    go get -u github.com/go-sql-driver/mysql github.com/gorilla/mux@latest && \
    go build

CMD ["go run main.go"]
