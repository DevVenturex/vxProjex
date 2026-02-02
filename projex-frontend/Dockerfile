FROM rust:latest as builder

WORKDIR /app

COPY Cargo.toml Cargo.lock ./
COPY projex-frontend ./peojex-frontend
COPY projex-backend ./projex-backend

WORKDIR /app/projex-frontend

RUN cargo install trunk
RUN trunk build --release

FROM nginx:alpine
COPY --from=builder /app/projex/frontend/dist /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]