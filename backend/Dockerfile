# Build stage
FROM golang:1.19 AS builder

WORKDIR /app

# Cache deps first
COPY go.mod go.sum ./
RUN go mod download

# Copy the rest of the code
COPY . .

# Build the Go app statically
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o backend-app main.go

# Final stage
FROM alpine:latest

WORKDIR /root/

# Copy binary from builder stage
COPY --from=builder /app/backend-app .

# Ensure it’s executable
RUN chmod +x backend-app

EXPOSE 8080

CMD ["./backend-app"]

