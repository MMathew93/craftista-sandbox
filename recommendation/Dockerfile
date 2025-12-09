# Build Stage
FROM golang:1.24-alpine AS builder

WORKDIR /app/recommendation

COPY go.mod go.sum ./

RUN go mod download

COPY . .

RUN CGO_ENABLED=0 go build -o worker

# Runtime build
FROM alpine:3.22

WORKDIR /app/recommendation

COPY --from=builder /app/recommendation/worker .
COPY --from=builder /app/recommendation/static ./static
COPY --from=builder /app/recommendation/templates ./templates
COPY --from=builder /app/recommendation/config.json .

CMD ["./worker"]