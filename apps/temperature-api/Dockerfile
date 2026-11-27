FROM golang:1.26-alpine AS build
WORKDIR /app
COPY go.mod main.go ./
RUN CGO_ENABLED=0 go build -o /temperature-api .

FROM scratch
COPY --from=build /temperature-api /temperature-api
USER 65532:65532
EXPOSE 8081
ENTRYPOINT ["/temperature-api"]
