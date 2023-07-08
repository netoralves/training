FROM registry.redhat.io/rhel8/go-toolset:latest

ENV QUOTES_VERSION=2.1 \
    SUMMARY="Famous Quotes" \
    DESCRIPTION="Famous Quotes is a PoC application for Go and MySQL"

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="Quotes 2.1" \
      io.openshift.expose-services="8000:quotes" \
      io.openshift.tags="poc,mysql,golang" \
      name="redhattraining/famous-quotes" \
      version="2.1" \
      usage="docker run -d -e QUOTES_USER=user -e QUOTES_PASSWORD=pass -e QUOTES_DATABASE=db -p 8000:8000 redhattraining/famous-quotes"

EXPOSE 8000

COPY . .

RUN go mod init example.com/main && \
    go get -u github.com/go-sql-driver/mysql github.com/gorilla/mux@latest && \
    go build

CMD ["go run main.go"]
