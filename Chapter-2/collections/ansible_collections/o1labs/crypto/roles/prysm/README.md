<p><img src="https://code.benco.io/icon-collection/logos/ansible.svg" alt="ansible logo" title="ansible" align="left" height="60" /></p>
<p><img src="https://prysmaticlabs.com/assets/PrysmStripe.png" alt="Prysm logo" title="prysm" align="right" height="60" /></p>

Ansible Role 🌠 🔗 Prysm
=========

Configure and operate Prysm: A full-featured client for the Ethereum 2.0 protocol, written in Go.

Requirements
------------

[Docker SDK](https://docker-py.readthedocs.io/en/stable/) for Python (for Python 2.6 support, use the deprecated `docker-py` library instead) or installation of the `docker` engine.

Role Variables
--------------

| var | description | default |
| :---: | :---: | :---: |
| *image* | Prysm client container image to deploy | `0labs/prysm:latest` |
| *prysm_config_dir* | configuration directory path within container | `/etc/prysm` |
| *eth2_chain* | Ethereum 2.0 chain to target during client helper operations | `prater` |
| *p2p_tcp_port* | peer-to-peer network communication and listening port | `13000` |
| *p2p_udp_port* | peer-to-peer network discovery port | `12000` |
| *eth2_api_port* | Ethereum 2.0 RESTful HTTP API listening port | `3501` |
| *beacon_rpc_port* | RPC port exposed by a beacon node | `4000` |
| *beacon_metrics_port* | port used to listen and respond to metrics requests for prometheus | `8080` |
| *validator_gateway_port* | gRPC gateway for JSON requests | `7500` |
| *validator_rpc_port* | RPC port exposed by a validator client | `7000` |
| *validator_metrics_port* | port used to listen and respond to metrics requests for prometheus | `8081` |
| *host_data_dir* | host directory to store node runtime/operational data | `/var/tmp/prysm` |
| *data_dir* | container directory to store node runtime/operational data | `/data` |
| *host_wallet_dir* | host directory to store node account wallets | `/var/tmp/prysm/wallets` |
| *host_keys_dir* | host directory to store node account keys | `/var/tmp/prysm/keys` |
| *beacon_env_file* | path to environment file to load by Beacon node container | `/var/tmp/prysm/.beacon.env` |
| *beacon_env_vars* | dict of beacon node client runtime environment settings (reference [here](https://github.com/0x0I/container-file-prysm#operations) for examples of available options) | `{}` |
| *validator_env_file* | Path to environment file to load by Validator container | `/var/tmp/prysm/.validator.env` |
| *validator_env_vars* | dict of validator client runtime environment settings (reference [here](https://github.com/0x0I/container-file-prysm#operations) for examples of available options) | `{}` |
| *setup_mode* | infrastructure provisioning setup mode (either `container` or `systemd` are supported) | `container` |
| *target_services* | list of services to include in deployment process (`beacon-node` and/or `validator`) | `["beacon-node", "validator"]` |
| *ops_runtime_dir* | operational directory to store runtime artifacts | `/var/tmp/prysm` |
| *restart_policy* | container restart policy | `unless-stopped` |
| *beacon_config* | beacon chain node configuration options settings (see [list](https://docs.prylabs.network/docs/prysm-usage/parameters/#beacon-node-configuration) of available config options) | `{}` **note:** reference `defaults/main.yml` |
| *validator_config* | validator client configuration options settings (see [list](https://docs.prylabs.network/docs/prysm-usage/parameters/#validator-configuration)) of available config options | `{}` **note:** reference `defaults/main.yml` |
| *cpus* | available CPU resources each deployed component can use | `1.0` |
| *memory* | available memory resources each deployed component can use | `4g` |
| *uninstall* | whether to remove installed components and artifacts | `false` |

Dependencies
------------
```
collections:
- name: community.docker
```
Example Playbook
----------------
```
- hosts: servers
  roles:
```

* Enable automatic acceptance of the terms of use when launching either a beacon-chain or validator node:
```
  - role: o1labs.crypto.prysm
    vars:
      beacon_config:
        accept-terms-of-use: true
```

* Launch a Prysm beacon-chain node connected to the Pyrmont Ethereum 2.0 testnet using a Goerli web3 Ethereum provider:
```
  - role: o1labs.crypto.prysm
    vars:
      beacon_config:
        http-web3provider: http://ethereum-rpc.goerli.01labs.net:8545
        pyrmont: true
```

* Customize the deploy container image and host + container node data directory:
```
  - role: o1labs.crypto.prysm
    vars:
      image: 0labs/prysm:v2.0.0
      host_data_dir=/my/host/data
      data_dir: /container/data/dir
```

* Install Eth2 deposit CLI tool and automatically setup multiple validator accounts/keys to register on the Prater testnet:
```
  - role: o1labs.crypto.prysm
    vars:
      setup_deposit_cli: true
      eth2_chain: prater
      deposit_cli_version: v1.2.0
      setup_deposit_accounts: true
      deposit_num_validators: 3
      deposit_key_password: ABCabc123!@#$
```

* Setup automatic cron backups of a localhost beacon-chain node DB every 12 hours (or twice a day):
```
  - role: o1labs.crypto.prysm
    vars:
      target_services: ["beacon-node']
      auto_backup_db: true
      backup_host_addr: http://localhost:8080
      backup_interval: "0 */12 * * *"
```

License
-------

MIT

Author Information
------------------

This Ansible role was created in 2021 by O1.IO.

🏆 **always happy to help & donations are always welcome** 💸

* **ETH (Ethereum):** 0x652eD9d222eeA1Ad843efec01E60C29bF2CF6E4c

* **BTC (Bitcoin):** 3E8gMxwEnfAAWbvjoPVqSz6DvPfwQ1q8Jn

* **ATOM (Cosmos):** cosmos19vmcf5t68w6ug45mrwjyauh4ey99u9htrgqv09
