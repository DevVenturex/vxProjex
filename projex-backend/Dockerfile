FROM rust:latest as builder

WORKDIR /app

COPY Cargo.toml Cargo.lock ./
COPY projex-backend ./projex-backend
COPY projex-frontend ./peojex-frontend

RUN cargo build --release

FROM debian:buster-slim
COPY --from=builder /app/target/release/projex-backend /usr/local/bin/projex-backend

EXPOSE 8080
CMD ["/usr/local/bin/projex-backend"]