# Stage 1: Build Stage
# Use the official Golang 1.18 image based on Alpine Linux to create a lightweight build environment
FROM golang:1.18-alpine AS builder

# Define the working directory inside the container for the build process
WORKDIR /app

# Copy Go module files to the container to allow for dependency management
COPY go.mod go.sum ./

# Download all the Go module dependencies specified in go.mod and go.sum
RUN go mod download

# Copy the rest of the application source code to the container for building
COPY . ./

# Compile the Go application and output the binary file named "main"
RUN go build -o main .

# Stage 2: Runtime Stage
# Use the official minimal Alpine image to create a small, efficient runtime environment
FROM alpine:latest

# Set the working directory inside the container for the runtime environment
WORKDIR /app

# Copy the compiled binary from the build stage to the runtime container
COPY --from=builder /app/main /app/main

# Expose port 8000 to allow external access to the application
EXPOSE 8000

# Set the default command to execute the binary when the container starts
CMD ["./main"]

