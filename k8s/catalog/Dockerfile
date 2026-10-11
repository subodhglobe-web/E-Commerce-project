
# Stage 1: Build the Go application
FROM golang:1.24-alpine AS builder

WORKDIR /app

# Copy Go dependency files
COPY go.mod go.sum ./

# Download dependencies
RUN go mod download

# Copy application source code
COPY . .

# Build the application
RUN CGO_ENABLED=0 GOOS=linux go build -o catalog-service .

# Stage 2: Run the application
FROM alpine:3.22

WORKDIR /app

# Copy the compiled binary from the builder stage
COPY --from=builder /app/catalog-service .

# Catalog application port
EXPOSE 8082

# Start the application
CMD ["./catalog-service"]

