# Use the official Go 1.21 image as the base for building
FROM golang:1.21 AS build

WORKDIR /app

COPY go.mod go.sum ./

RUN go mod download

COPY . .

RUN CGO_ENABLED=0 go build -o auth-api

# Use a smaller base image for the final container (no Go runtime needed)
FROM debian:bookworm-slim

WORKDIR /app

COPY --from=build /app/auth-api .
RUN chmod +x ./auth-api

EXPOSE ${AUTH_API_PORT:-8081}

ENV AUTH_API_PORT=8081

# Run the binary when the container starts
CMD ["./auth-api"]
