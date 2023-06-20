# Web3Signer/Hashicorp (via Agent) docker compose

- Make sure Hashicorp docker compose is up (using different terminal window). See [README](./vault/README.md) for more details.
```
cd ./vault
docker compose up
```

## Generate Hashicorp configuration for Web3Signer if required.

Assuming that vault agent is up and running and listening on port 8200 using above docker compose file, use following commands to generate `n`
random BLS keys, import it in Hashicorp and generate Web3Signer configuration files. The config files will be generated in `web3signer/config/keys`

```
git submodule update --init --recursive
./scripts/gen-keys.sh 20000
```

## Run Web3Signer
Assuming that the above step is performed to generate configuration files and vault docker compose is up.

```
cd ./web3signer
docker compose up
```

## Clean up
- In vault and web3signer terminal windows, `CTRL+C` and/or `docker compose down`.
- To remove docker images, generated keys, hashicorp cert, data, cred, configuration files. run `./scripts/clear-all.sh`