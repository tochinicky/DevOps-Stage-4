FROM golang:1.21 AS builder
WORKDIR /app
COPY . .
RUN CGO_ENABLED=0 GOOS=linux GOARCH=arm64 go build -o auth-api  # Statically linked binary

FROM alpine:latest
WORKDIR /root/
COPY --from=builder /app/auth-api .
RUN chmod +x /root/auth-api
EXPOSE 8081
CMD ["./auth-api"]