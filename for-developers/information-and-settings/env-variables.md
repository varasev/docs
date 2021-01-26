# ENV Variables

{% hint style="info" %}
This table is horizontally scrollable, version information is located in the last column.
{% endhint %}

{% hint style="info" %}
Additional information related to certain variables is available on the [ansible deployment](../ansible-deployment/) page.
{% endhint %}

{% hint style="info" %}
You will find deprecated ENV vars in [Deprecated ENV Variables](https://docs.blockscout.com/for-developers/information-and-settings/deprecated-env-variables) chapter
{% endhint %}

* To set variables using the CLI, use the export command. For example:

  ```bash
  $ export ETHEREUM_JSONRPC_VARIANT=parity
  $ export COIN=POA
  $ export NETWORK=POA
  ```

| Variable | Required | Description | Default | Version | Need recompile |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `NETWORK` | ✅ | Environment variable for the main EVM network such as Ethereum or POA | POA | all |  |
| `SUBNETWORK` | ✅ | Environment variable for the subnetwork such as Core or Sokol Network. This will be displayed as selected in the chains list dropdown. | POA Sokol | all |  |
| `LOGO` | ✅ | Environment variable for the header logo image location. The logo files names for different chains can be found [here](https://github.com/poanetwork/blockscout/tree/master/apps/block_scout_web/assets/static/images) | /images/blockscout\_logo.svg | all |  |
| `LOGO_FOOTER` | ✅ | Environment variable for the footer logo image location. The logo files names for different chains can be found [here](https://github.com/poanetwork/blockscout/tree/master/apps/block_scout_web/assets/static/images) | /images/blockscout\_logo.svg |  |  |
| `ETHEREUM_JSONRPC_VARIANT` | ✅ | Tells the application which RPC Client the node is using \(i.e. `geth`, `parity`, `besu`, or `ganache`\) \([See Client Settings for more info](client-settings-parity-geth-ganache.md)\) | parity | all |  |
| `ETHEREUM_JSONRPC_HTTP_URL` | ✅ | The RPC endpoint used to fetch blocks, transactions, receipts, tokens. | localhost:8545 | all |  |
| `ETHEREUM_JSONRPC_TRACE_URL` |  | The RPC endpoint specifically for the Geth/Parity/Besu client used by trace\_block and trace\_replayTransaction. This can be used to designate a tracing node. | localhost:8545 | all |  |
| `ETHEREUM_JSONRPC_WS_URL` | ✅ | The WebSockets RPC endpoint used to subscribe to the `newHeads` subscription alerting the indexer to fetch new blocks. | ws://localhost:8546 | all |  |
| `ETHEREUM_JSONRPC_TRANSPORT` |  | Specifies the transport for Blockscout to connect to the Ethereum Node. Available transports are `http` and `ipc`. If `ipc` is selected, also set `IPC_PATH` variable | http | v3.1.0+ |  |
| `IPC_PATH` |  | Path to the IPC file of the running node if IPC transport is chosen | \(empty\) | v2.1.1+ |  |
| `NETWORK_PATH` |  | Used to set a network path other than what is displayed in the root directory. An example would be to add `/eth/mainnet/` to the root directory. | / | all |  |
| `API_PATH` |  | PATH in API endpoint URL at API docs page | / | v3.1.0+ |  |
| `SOCKET_ROOT` |  | Custom websocket path | \(empty\) | v3.0.0+ |  |
| `BLOCKSCOUT_HOST` |  | Host for API endpoint examples | localhost | v2.1.0+ |  |
| `BLOCKSCOUT_PROTOCOL` |  | Url scheme for blockscout | in prod env `https` is used, in dev env `http` is used | v2.1.0+ |  |
| `SECRET_KEY_BASE` | ✅ | Use mix phx.gen.secret to generate a new Secret Key Base string to protect production assets. | \(empty\) | all |  |
| `CHECK_ORIGIN` |  | Used to check the origin of requests when the origin header is present. It defaults to `false`. In case of true, it will check against the host value. | false | all |  |
| `PORT` | ✅ | Default port the application runs on is 4000 | 4000 | all |  |
| `COIN` | ✅ | The coin here is checked via the CoinGecko API to obtain USD prices on graphs and other areas of the UI | POA | all |  |
| `COINGECKO_COIN_ID` |  | Explicitly set CoinGecko coin ID | \(empty\) | v3.1.2+ |  |
| `METADATA_CONTRACT` |  | This environment variable is specifically used by POA Network to obtain Validators information to display in the UI. | \(empty\) | all |  |
| `VALIDATORS_CONTRACT` |  | This environment variable is specifically used by POA Network to obtain the list of current validators. | \(empty\) | all |  |
| `KEYS_MANAGER_CONTRACT` |  | This environment variable is specifically used by POA Network to set KeysManager proxy contract in order to obtain payout key by mining key. This need to identify distributed reward to the validator. | \(empty\) | v3.1.2+ |  |
| `REWARDS_CONTRACT` |  | Emission rewards contract address. This env var is used only if `EMISSION_FORMAT` is set to `POA` | `0xeca443e8e1ab29971a45a9c57a6a9875701698a5` | v2.0.4+ |  |
| `TOKEN_BRIDGE_CONTRACT` |  | Token bridge proxy contract. For \`TokenBridge\` supply module. | `0x7301CFA0e1756B71869E93d4e4Dca5c7d0eb0AA6` | v1.3.2+ |  |
| `EMISSION_FORMAT` |  | Should be set to `POA` if you have block emission identical to POA Network. This env var is used only if `CHAIN_SPEC_PATH` is set | `DEFAULT` | v2.0.4+ |  |
| `CHAIN_SPEC_PATH` |  | Chain specification path \(absolute file system path or URL\) to import block emission reward ranges and genesis account balances from. Geth- and OpenEthereum-style specs are supported. | \(empty\) | v2.0.4+ |  |
| `SUPPLY_MODULE` |  | This environment variable is used by the xDai Chain/RSK in order to tell the application how to calculate the total supply of the chain. Available values are `TokenBridge`, `RSK` | \(empty\) | all |  |
| `SOURCE_MODULE` |  | This environment variable is used to calculate the exchange rate and is specifically used by the xDai Chain. Available value is `TokenBridge` | \(empty\) | all |  |
| `DATABASE_URL` | ✅ | Variable to define the Database endpoint. | \(empty\) | all |  |
| `POOL_SIZE` |  | Production environment variable to define the number of database connections allowed. | 20 | all |  |
| `ECTO_USE_SSL` |  | Production environment variable to use SSL on Ecto queries. | true | all |  |
| `DATADOG_HOST` |  | Host configuration setting for [Datadog integration](https://docs.datadoghq.com/integrations/) | \(empty\) | all |  |
| `DATADOG_PORT` |  | Port configuration setting for [Datadog integration](https://docs.datadoghq.com/integrations/). | \(empty} | all |  |
| `SPANDEX_BATCH_SIZE` |  | [Spandex](https://github.com/spandex-project/spandex) and Datadog configuration setting. | \(empty\) | all |  |
| `SPANDEX_SYNC_THRESHOLD` |  | [Spandex](https://github.com/spandex-project/spandex) and Datadog configuration setting. | \(empty\) | all |  |
| `HEART_BEAT_TIMEOUT` |  | Production environment variable to restart the application in the event of a crash. | 30 | all |  |
| `HEART_COMMAND` |  | Production environment variable to restart the application in the event of a crash. | systemctl restart explorer.service | all |  |
| `BLOCKSCOUT_VERSION` |  | Added to the footer to signify the current BlockScout version. | \(empty\) | v1.3.4+ |  |
| `RELEASE_LINK` |  | The link to Blockscout release notes in the footer. | https: //github.com/poanetwork/  blockscout/releases/   tag/${BLOCKSCOUT\_VERSION} | v1.3.5+ |  |
| `ELIXIR_VERSION` |  | Elixir version to install on the node before Blockscout deploy. It is used in bash script in Terraform / Ansible deployment script | \(empty\) | all |  |
| `BLOCK_TRANSFORMER` |  | Transformer for blocks: base or clique. | base | v1.3.4+ |  |
| `GRAPHIQL_TRANSACTION` |  | Default transaction hash in a sample query to GraphiQL. | \(empty\) | v1.2.0+ | ✅ |
| `FIRST_BLOCK` |  | The block number, where indexing begins from. | 0 | v1.3.8+ |  |
| `LAST_BLOCK` |  | The block number, where indexing stops. | \(empty\) | v2.0.3+ |  |
| `LINK_TO_OTHER_EXPLORERS` |  | true/false. If true, links to other explorers are added in the footer | \(empty\) | v1.3.0+ |  |
| `OTHER_EXPLORERS` |  | The list of alternative explorers. This env var was introduced in PR [\#3414](https://github.com/poanetwork/blockscout/pull/3414). | \(empty\) | v3.4.0+ |  |
| `SUPPORTED_CHAINS` |  | An array of supported chains that display in the footer and in the chains dropdown. This var was introduced in this PR [\#1900](https://github.com/poanetwork/blockscout/pull/1900) and looks like an array of JSON objects. | \(empty\) | v2.0.0+ |  |
| `BLOCK_COUNT_CACHE_PERIOD` |  | time to live of blocks with consensus count cache in seconds. This var was introduced in [\#1876](https://github.com/poanetwork/blockscout/pull/1876) | 2 hours | v2.0.0+ |  |
| `TXS_COUNT_CACHE_PERIOD` |  | Interval in seconds to restart the task, which calculates the total txs count. | 2 hours | v1.3.9+ |  |
| `ADDRESS_COUNT_CACHE_PERIOD` |  | time to live of cache in seconds. This var was introduced in [\#2822](https://github.com/poanetwork/blockscout/pull/2822) | 2 hours | v2.1.1+ |  |
| `ADDRESS_SUM_CACHE_PERIOD` |  | time to live of addresses sum \(except burn address\) cache in seconds. This var was introduced in [\#2862](https://github.com/poanetwork/blockscout/pull/2862) | 1 hour | v2.1.1+ |  |
| `TOTAL_GAS_USAGE_CACHE_PERIOD` |  | Interval in seconds to restart the task, which calculates the total gas usage. | 2 hours | v3.4.0+ |  |
| `ADDRESS_TRANSACTIONS_GAS_USAGE_COUNTER_CACHE_PERIOD` |  | Interval in seconds to restart the task, which calculates gas usage at the address. | 30 minutes | v3.4.0+ |  |
| `TOKEN_HOLDERS_COUNTER_CACHE_PERIOD` |  | Interval in seconds to restart the task, which calculates holders count of the token. | 1 hour | v3.4.0+ |  |
| `TOKEN_TRANSFERS_COUNTER_CACHE_PERIOD` |  | Interval in seconds to restart the task, which calculates transfers count of the token. | 1 hour | v3.4.0+ |  |
| `ADDRESS_WITH_BALANCES_UPDATE_INTERVAL` |  | Interval in seconds to restart the task, which calculates addresses with balances. | 30 minutes | v1.3.9+ |  |
| `TOKEN_METADATA_UPDATE_INTERVAL` |  | Interval in seconds to restart the task which updates token metadata | 60 \* 60 \* 24 _\*_ 2 | v2.0.1+ |  |
| `AVERAGE_BLOCK_CACHE_PERIOD` |  | Update of average block period cache, in seconds | 30 minutes | v2.0.2+ |  |
| `MARKET_HISTORY_CACHE_PERIOD` |  | Update of market history cache, in seconds | 6 hours | v2.0.2+ |  |
| `ALLOWED_EVM_VERSIONS` |  | the comma-separated list of allowed EVM versions for contracts verification. This var was introduced in [\#1964](https://github.com/poanetwork/blockscout/pull/1964) | "homestead, tangerineWhistle, spuriousDragon, byzantium, constantinople, petersburg" | v2.0.0+ |  |
| `UNCLES_IN_AVERAGE_BLOCK_TIME` |  | Include or exclude non-consensus blocks in avg block time calculation. Exclude if `false`. | false | v2.0.1+ |  |
| `DISABLE_WEBAPP` |  | If `true`, endpoints to webapp are hidden \(compile-time\). Also, enabling it makes notifications go through `db_notify` | `false` | v2.0.3+ | ✅ |
| `DISABLE_READ_API` |  | If `true`, read-only endpoints to API are hidden \(compile-time\) | `false` | v2.0.3+ | ✅ |
| `DISABLE_WRITE_API` |  | If `true`, write endpoints to API are hidden \(compile-time\) | `false` | v2.0.3+ | ✅ |
| `DISABLE_INDEXER` |  | If `true`, indexer application doesn't run | `false` | v2.0.3+ | ✅ |
| `WEBAPP_URL` |  | Link to web application instance, e.g. `protocol://host/path` | \(empty\) | v2.0.3+ |  |
| `API_URL` |  | Link to API instance, e.g. `protocol://host/path` | \(empty\) | v2.0.3+ |  |
| `WOBSERVER_ENABLED` |  | If `true` enables wobserver interface | \(empty\) | v3.3.2+ | ✅ |
| `SHOW_ADDRESS_MARKETCAP_PERCENTAGE` |  | Configures market cap percentage column on the top accounts page | `true` | v2.1.1+ |  |
| `CHECKSUM_ADDRESS_HASHES` |  | If set to `true`, redirects to checksummed version of address hashes | true | v3.1.0+ |  |
| `CHECKSUM_FUNCTION` |  | Defines checksum address function. 2 available values: `rsk`, `eth` | eth | v2.0.1+ |  |
| `DISABLE_EXCHANGE_RATES` |  | Disables or enables fetching of coin price from Coingecko API | false | v3.1.2+ |  |
| `DISABLE_KNOWN_TOKENS` |  | Disables or enables token symbol for known contract | false | v3.4.0+ |  |
| `ENABLE_TXS_STATS` |  | Disables or enables txs per day stats gathering | false | v3.1.2+ |  |
| `SHOW_PRICE_CHART` |  | Disables or enables price and market cap of coin charts on the main page | false | v3.1.2+ |  |
| `SHOW_TXS_CHART` |  | Disables or enables txs count per day chart on the main page | false | v3.1.2+ |  |
| `HISTORY_FETCH_INTERVAL` |  | Interval in minutes how often to request count of txs per current day in order to display txs count per day chart on the main page | 60 | v3.1.2+ |  |
| `TXS_HISTORIAN_INIT_LAG` |  | The initial delay in minutes in txs count history fetching in order to display txs count per day history chart on the main page | 0 | v3.1.2+ |  |
| `TXS_STATS_DAYS_TO_COMPILE_AT_INIT` |  | Number of days for fetching of history of txs count per day in order to display it in txs count per day history chart on the main page | 365 | v3.1.2+ |  |
| `COIN_BALANCE_HISTORY_DAYS` |  | Number of days to consider at coin balance history chart | 10 | v3.1.3+ |  |
| `APPS_MENU` |  | true/false. If true, the Apps navigation menu item appears | false | v3.3.1+ |  |
| `EXTERNAL_APPS` |  | An array of external apps to display in Apps menu item. This var was introduced in this PR [\#3184](https://github.com/poanetwork/blockscout/pull/3184) and looks like an array of JSON objects. | \(empty\) | v3.3.1+ |  |
| `OMNI_BRIDGE_MEDIATOR` |  | An address of OmniBridge mediator to bridge multiple tokens. Providing this address enables bridged tokens functionality: bridged status and link to the original token in the foreign chain. | \(empty\) | v3.3.2+ |  |
| `AMB_BRIDGE_MEDIATORS` |  | A comma-separated list of AMB extensions' mediators' addresses' hashes to fetch bridged tokens through those mediators. | \(empty\) | v3.3.3+ |  |
| `GAS_PRICE` |  | Gas price in Gwei. If the variable is present, gas price displays at the main page | \(empty\) | v3.3.2+ |  |
| `FOREIGN_JSON_RPC` |  | JSON RPC endpoint to the foreign chain in order to get metadata of bridged through Omni-bridge token. It was introduced in this PR [\#3282](https://github.com/poanetwork/blockscout/pull/3282) | \(empty\) | v3.3.3+ |  |
| `BRIDGE_MARKET_CAP_UPDATE_INTERVAL` |  | Market cap update interval for \`TokenBridge\` supply module as for TokenBridge and for OmniBridge as well, in seconds. It was introduced in this PR [\#3293](https://github.com/poanetwork/blockscout/pull/3293) | 30 minutes | v3.3.3+ |  |
| `RESTRICTED_LIST` |  | A comma-separated list of addresses to enable restricted access on them | \(empty\) | v3.3.3+ |  |
| `RESTRICTED_LIST_KEY` |  | A key to access  addresses listed in`RESTRICTED_LIST` variable. Can be passed via query param to the page's URL: `?key=...` | \(empty\) | v3.3.3+ |  |
| `ADDRESS_TRANSACTIONS_CACHE_PERIOD` |  | time to live of address' transactions counter in seconds. This var was introduced in [\#3330](https://github.com/poanetwork/blockscout/pull/3330) | 1 hour | v3.4.0+ |  |
| `DISABLE_BRIDGE_MARKET_CAP_UPDATER` |  | Disables recurring consolidation of TokenBridge market cap from TokenBridge, OmniBridge and AMB extensions | \(empty\) | v3.3.3+ |  |
| `POS_STAKING_CONTRACT` |  | The address of POSDAO staking contract. When provided, enables staking DApp. ValidatorSet and BlockReward contract addresses are fetched using corresponding getters. | \(empty\) | v3.4.0+ |  |
| `POS_ETH_SUBSCRIBE_MAX_DELAY` |  | Used by the staking DApp. The number of seconds of max delay after the latest block number arrived from eth_subscribe. Once this time is elapsed, the staking DApp automatically switches to eth_blockNumber which then is requested every `POS_ETH_BLOCKNUMBER_PULL_INTERVAL` milliseconds until eth_subscribe works again. | 60 | master |  |
| `POS_ETH_BLOCKNUMBER_PULL_INTERVAL` |  | An interval between eth_blockNumber requests (in milliseconds) made by staking DApp to retrieve a new block number. Used when eth_subscribe stops working. | 500 | master |  |
| `TOKEN_EXCHANGE_RATE_CACHE_PERIOD` |  | Managing of cache invalidation for token's exchange rate. | \(empty\) | v3.5.0+ |  |
| `ADDRESS_TOKENS_USD_SUM_CACHE_PERIOD` |  | Managing of cache invalidation period for the sum of USD value of tokens per tokens' holder address | \(empty\) | v3.5.0+ |  |

