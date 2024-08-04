FROM --platform=linux/amd64 ubuntu:20.04

# Install dependencies
RUN apt-get update && apt-get install -y \
    wget \
    tar \
    libc6 \
    libstdc++6 \
    zlib1g \
    && rm -rf /var/lib/apt/lists/*

# Download and install Bitcoin Core
RUN wget https://bitcoincore.org/bin/bitcoin-core-26.0/bitcoin-26.0-x86_64-linux-gnu.tar.gz && \
    tar -xvf bitcoin-26.0-x86_64-linux-gnu.tar.gz && \
    chmod +x bitcoin-26.0/bin/bitcoind && \
    chmod +x bitcoin-26.0/bin/bitcoin-cli && \
    mv bitcoin-26.0 /usr/local/bitcoin && \
    rm bitcoin-26.0-x86_64-linux-gnu.tar.gz

# Create bitcoin data directory
RUN mkdir /bitcoin-data

# Expose the port
EXPOSE 38332

# Run bitcoind with command-line options
CMD ["/usr/local/bitcoin/bin/bitcoind", "-signet", "-server", "-deprecatedrpc=create_bdb", "-rpcport=38332", "-rpcuser=${BITCOIN_RPC_USER}", "-rpcpassword=${BITCOIN_RPC_PASSWORD}", "-rpcallowip=0.0.0.0/0", "-rpcbind=0.0.0.0", "-datadir=/bitcoin-data"]
