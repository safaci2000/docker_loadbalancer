FROM tutum/nginx

# Install wget and install/updates certificates
RUN apt-get update \
 && apt-get install -y -q --no-install-recommends \
    ca-certificates \
    wget \
    build-essential \
    openssl \
    libssl-dev \
    ruby-full \
 && apt-get clean \
 && rm -r /var/lib/apt/lists/*

# Generate Default Self-signed certificate
RUN openssl genrsa -des3 -passout pass:x -out default.pass.key 2048 \
 && openssl rsa -passin pass:x -in default.pass.key -out default.key \
 && rm default.pass.key \
 && openssl req -new -key default.key -out default.csr -subj "/C=UK/ST=State/L=local/O=OrgName/OU=Web/CN=example.com" \
 && openssl x509 -req -days 365 -in default.csr -signkey default.key -out default.crt \
 && mkdir -p /etc/nginx/certs/ \
 && mv default.crt /etc/nginx/certs/default.crt && mv default.key /etc/nginx/certs/default.key
 # Then, just use the generated default.key and default.crt files.

ADD sites-enabled/ /etc/nginx/sites-enabled
