FROM nginx:alpine

# Install OpenSSL for generating certificates
RUN apk add --no-cache openssl

# Define directories
RUN mkdir -p /etc/nginx/certs

# Generate a self-signed certificate for `arfprince.dev`
RUN openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout /etc/nginx/certs/arfprince.dev.key \
  -out /etc/nginx/certs/arfprince.dev.crt \
  -subj "/C=US/ST=State/L=City/O=Organization/CN=arfprince.dev" && \
  ls -l /etc/nginx/certs

# Copy the custom nginx configuration
COPY nginx.conf /etc/nginx/nginx.conf

# Expose HTTP and HTTPS ports
EXPOSE 443

CMD ["nginx", "-g", "daemon off;"]
