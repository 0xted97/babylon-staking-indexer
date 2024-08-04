# Start bitcoin node
- docker-compose -f ./bitcoind/docker-compose.yml up --build

# Start  RabbitMQ
- cd ../ (move to root folder)
- docker-compose -f ./bitcoind/docker-compose.yml up --build

# Start Staking Indexer
- sid init --home ./integration
- sid start --home ./integration --start-height 197535 --params-path ./integration/global-params.json


# Start Staking api
# Start Bloom API