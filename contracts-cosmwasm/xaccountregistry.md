# xAccountRegistry

## Contract State

### `Config`

Stores the contract configuration.&#x20;

{% tabs %}
{% tab title="Rust" %}
```rust
pub const CONFIG: Item<Config>
```

| Type   | Description            |
| ------ | ---------------------- |
| Config | Contract configuration |

```rust
pub struct Config {
    pub wormhole_id_here: u64, 
    pub wormhole_core_here: Addr, 
    pub owner: Addr, 
    pub factory_code_id: u64, 
    pub x_account_code_id: u64, 
}
```

| Key                  | Type | Description |
| -------------------- | ---- | ----------- |
| `wormhole_id_here`   | u64  |             |
| `wormhole_core_here` | Addr |             |
| `owner`              | Addr |             |
| `factory_code_id`    | u64  |             |
| `x_account_code_id`  | u64  |             |
{% endtab %}
{% endtabs %}



### `ChainInfos`

Stores xAccount / Wormhole information of supported chains.&#x20;

{% tabs %}
{% tab title="Rust" %}
```rust
pub const CHAIN_INFOS: Map<u64, ChainInfo>
```

| Type      | Description                     |
| --------- | ------------------------------- |
| u64       | Wormhole ID of chain            |
| ChainInfo | xAccount / Wormhole information |

```rust
pub struct ChainInfo {
    pub wormhole_id: u64, 
    pub wormhole_core: String, 
    pub x_account_registry: String, 
    pub x_account_factory: String, 
}
```

| Key                  | Type   | Description |
| -------------------- | ------ | ----------- |
| `wormhole_id`        | u64    |             |
| `wormhole_core`      | String |             |
| `x_account_registry` | String |             |
| `x_account_factory`  | String |             |
{% endtab %}
{% endtabs %}



### `VaaArchive`

Stores

{% tabs %}
{% tab title="Rust" %}
```rust
pub const VAA_ARCHIVE: Map<&[u8], bool>
```

| Type   | Description |
| ------ | ----------- |
| &\[u8] |             |
| bool   |             |
{% endtab %}
{% endtabs %}



## InstantiateMsg

{% tabs %}
{% tab title="Rust" %}
```rust
pub struct InstantiateMsg {
    pub wormhole_id_here: u64, 
    pub wormhole_core_contract: String, 
    pub factory_code_id: u64, 
    pub x_account_code_id: u64, 
}
```

| Key                      | Type   | Description                                             |
| ------------------------ | ------ | ------------------------------------------------------- |
| `wormhole_id_here`       | u64    | Wormhole ID of blockchain where the registry resides on |
| `wormhole_core_contract` | String | Wor                                                     |
| `factory_code_id`        | u64    |                                                         |
| `x_account_code_id`      | u64    |                                                         |
{% endtab %}

{% tab title="JSON" %}
```json
{
  "wormhole_id_here": 19, 
  "wormhole_core_contract": "inj1...", 
  "factory_code_id": 1, 
  "x_account_code_id": 2, 
}
```

| Key                      | Type   | Description |
| ------------------------ | ------ | ----------- |
| `wormhole_id_here`       | u64    |             |
| `wormhole_core_contract` | String |             |
| `factory_code_id`        | u64    |             |
| `x_account_code_id`      | u64    |             |
{% endtab %}
{% endtabs %}



## ExecuteMsg

### `UpdateConfig`

Updates the contract configuration.&#x20;

{% tabs %}
{% tab title="Rust" %}
```rust
pub enum ExecuteMsg {
    UpdateConfig {
        wormhole_id_here: Option<u64>, 
        owner: Option<String>, 
    }
}
```

| Key                  | Type   | Description |
| -------------------- | ------ | ----------- |
| `wormhole_id_here`\* | u64    |             |
| `owner`\*            | String |             |

\* = optional
{% endtab %}

{% tab title="JSON" %}
```json
{
  "update_config": {
    "wormhole_id_here": 19, 
    "owner": "inj1..." 
  }
}
```

| Key                  | Type   | Description |
| -------------------- | ------ | ----------- |
| `wormhole_id_here`\* | u64    |             |
| `owner`\*            | String |             |

\* = optional
{% endtab %}
{% endtabs %}



### `UpsertChainInfo`

Adds information about a newly supported chain.&#x20;

{% tabs %}
{% tab title="Rust" %}
```rust
pub enum ExecuteMsg {
    UpsertChainInfo {
        chain_info: ChainInfo, 
    }
}
```

| Key          | Type      | Description               |
| ------------ | --------- | ------------------------- |
| `chain_info` | ChainInfo | Chain network information |
{% endtab %}

{% tab title="JSON" %}
```json
{
  "upsert_chain_info": {
    "chain_info": {}
  }
}
```

| Key          | Type      | Description               |
| ------------ | --------- | ------------------------- |
| `chain_info` | ChainInfo | Chain network information |
{% endtab %}
{% endtabs %}



### `UpdateFactory`

Updates stored xAccountFactory's code ID to the specified code ID. Also migrates existing xAccountFactory contract to the new code ID.&#x20;

{% tabs %}
{% tab title="Rust" %}
```rust
pub enum ExecuteMsg {
    UpdateFactory {
        factory_code_id: u64, 
        migrate_msg: Binary
    }
}
```

| Key               | Type   | Description                       |
| ----------------- | ------ | --------------------------------- |
| `factory_code_id` | u64    | Code ID of new xAccountFactory    |
| `migrate_msg`     | Binary | MigrateMsg of new xAccountFactory |
{% endtab %}

{% tab title="JSON" %}
```json
{
  "update_factory": {
    "factory_code_id": 13, 
    "migrate_msg": "eyJiZWFybWFya2V0IjoibGFicyJ9"
  }
}
```

| Key               | Type   | Description                       |
| ----------------- | ------ | --------------------------------- |
| `factory_code_id` | u64    | Code ID of new xAccountFactory    |
| `migrate_msg`     | Binary | MigrateMsg of new xAccountFactory |
{% endtab %}
{% endtabs %}



## QueryMsg

### `Config`

Gets the contract configuration.&#x20;

{% tabs %}
{% tab title="Rust" %}
#### Request

```rust
pub enum QueryMsg {
    Config {}
}
```

| Key | Type | Description |
| --- | ---- | ----------- |
|     |      |             |

#### Response

```rust
pub struct ConfigResponse {
    pub wormhole_id_here: u64, 
    pub wormhole_core_here: String, 
    pub owner: String, 
    pub factory_code_id: u64, 
    pub x_account_code_id: u64, 
}
```

| Key                  | Type   | Description |
| -------------------- | ------ | ----------- |
| `wormhole_id_here`   | u64    |             |
| `wormhole_core_here` | String |             |
| `owner`              | String |             |
| `factory_code_id`    | u64    |             |
| `x_account_code_id`  | u64    |             |
{% endtab %}

{% tab title="JSON" %}
#### Request

```json
{
  "config": {}
}
```

| Key | Type | Description |
| --- | ---- | ----------- |
|     |      |             |

#### Response

```json
{
  "wormhole_id_here": 19, 
  "wormhole_core_here": "inj1...", 
  "owner": inj1...", 
  "factory_code_id": 23, 
  "x_account_code_id": 26, 
}
```

| Key                  | Type   | Description |
| -------------------- | ------ | ----------- |
| `wormhole_id_here`   | u64    |             |
| `wormhole_core_here` | String |             |
| `owner`              | String |             |
| `factory_code_id`    | u64    |             |
| `x_account_code_id`  | u64    |             |
{% endtab %}
{% endtabs %}



### `ChainInfo`

Gets xAccount / Wormhole information of the registry's residing chain.&#x20;

{% tabs %}
{% tab title="Rust" %}
#### Request

```rust
pub enum QueryMsg {
    ChainInfo {}
}
```

| Key | Type | Description |
| --- | ---- | ----------- |
|     |      |             |

#### Response

```rust
pub struct ChainInfo {
    pub wormhole_id: u64, 
    pub wormhole_core: String, 
    pub x_account_registry: String, 
    pub x_account_factory: String, 
}
```

| Key                  | Type   | Description |
| -------------------- | ------ | ----------- |
| `wormhole_id`        | u64    |             |
| `wormhole_core`      | String |             |
| `x_account_registry` | String |             |
| `x_account_factory`  | String |             |
{% endtab %}

{% tab title="JSON" %}
#### Request

```json
{
  "chain_info": {}
}
```

| Key | Type | Description |
| --- | ---- | ----------- |
|     |      |             |

#### Response

```json
{
  "wormhole_id": 19, 
  "wormhole_core": "inj1...", 
  "x_account_registry": "inj1...", 
  "x_account_factory": "inj1..." 
}
```

| Key                  | Type   | Description |
| -------------------- | ------ | ----------- |
| `wormhole_id`        | u64    |             |
| `wormhole_core`      | String |             |
| `x_account_registry` | String |             |
| `x_account_factory`  | String |             |
{% endtab %}
{% endtabs %}



### `ChainInfos`

Gets xAccount / Wormhole information of all chains.&#x20;

{% tabs %}
{% tab title="Rust" %}
#### Request

```rust
pub enum QueryMsg {
    ChainInfos {
        start_after: Option<u64>, 
        limit: Option<u64>, 
    }
}
```

| Key             | Type | Description |
| --------------- | ---- | ----------- |
| `start_after`\* | u64  |             |
| `limit`\*       | u64  |             |

\* = optional

#### Response

```rust
Vec<ChainInfo>
```

| Type      | Description |
| --------- | ----------- |
| ChainInfo |             |

```rust
pub struct ChainInfo {
    pub wormhole_id: u64, 
    pub wormhole_core: String, 
    pub x_account_registry: String, 
    pub x_account_factory: String, 
}
```

| Key                  | Type   | Description |
| -------------------- | ------ | ----------- |
| `wormhole_id`        | u64    |             |
| `wormhole_core`      | String |             |
| `x_account_registry` | String |             |
| `x_account_factory`  | String |             |
{% endtab %}

{% tab title="JSON" %}
#### Request

```json
{
  "chain_infos": {
    "start_after": , 
    "limit": 
  }
}
```

| Key             | Type | Description |
| --------------- | ---- | ----------- |
| `start_after`\* |      |             |
| `limit`\*       |      |             |

\* = optional

#### Response

```
{
  [
    {
    
    }, 
    {
    
    }
  ]
}
```

| Key                  | Type   | Description |
| -------------------- | ------ | ----------- |
| `wormhole_id`        | u64    |             |
| `wormhole_core`      | String |             |
| `x_account_registry` | String |             |
| x\_account\_factory  | String |             |
{% endtab %}
{% endtabs %}



### `MigrateMsg`

{% tabs %}
{% tab title="Rust" %}
```
// Some code
```

| Key | Type | Description |
| --- | ---- | ----------- |
|     |      |             |
|     |      |             |
|     |      |             |
{% endtab %}

{% tab title="JSON" %}
```
// Some code
```

| Key | Type | Description |
| --- | ---- | ----------- |
|     |      |             |
|     |      |             |
|     |      |             |
{% endtab %}
{% endtabs %}
