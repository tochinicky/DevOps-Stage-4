FROM golang:1.21 as builder
WORKDIR /app
COPY . .
RUN go build -o auth-api

FROM alpine:latest
WORKDIR /root/
COPY --from=builder /app/auth-api .
EXPOSE 8081
CMD ["./auth-api"]