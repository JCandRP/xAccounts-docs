# xAccountFactory

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
    pub registry_address: Addr, 
}
```

| Key                | Type | Description                          |
| ------------------ | ---- | ------------------------------------ |
| `registry_address` | Addr | Contract address of xAccountRegistry |
{% endtab %}
{% endtabs %}



### `VaaArchive`

Archive of VAAs.&#x20;

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
    pub registry_address: String, 
}
```

| Key                | Type   | Description                          |
| ------------------ | ------ | ------------------------------------ |
| `registry_address` | String | Contract address of xAccountRegistry |
{% endtab %}

{% tab title="JSON" %}
```json
{
  "registry_address": "inj1..."
}
```

| Key                | Type   | Description                          |
| ------------------ | ------ | ------------------------------------ |
| `registry_address` | String | Contract address of xAccountRegistry |
{% endtab %}
{% endtabs %}



## ExecuteMsg

### `CreateXAccounts`

Deploys a new xAccount pair.&#x20;

{% tabs %}
{% tab title="Rust" %}
```rust
pub enum ExecuteMsg {
    CreateXAccounts {
        chain_ids: Vec<u64>, 
        initial_master: AccountInfo, 
    }
}
```

| Key              | Type        | Description |
| ---------------- | ----------- | ----------- |
| `chain_ids`      | Vec\<u64>   |             |
| `initial_master` | AccountInfo |             |
{% endtab %}

{% tab title="JSON" %}
```json
{
  "create_x_accounts": {
    "chain_ids": [0, 1, 2, 3]
    "initial_master": {}
  }
}
```

| Key              | Type        | Description |
| ---------------- | ----------- | ----------- |
| `chain_ids`      | Vec\<u64>   |             |
| `initial_master` | AccountInfo |             |
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
    pub registry_address: String, 
}
```

| Key                | Type   | Description                          |
| ------------------ | ------ | ------------------------------------ |
| `registry_address` | String | Contract address of xAccountRegistry |
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
  "registry_address": "inj1..."
}
```

| Key                | Type   | Description                          |
| ------------------ | ------ | ------------------------------------ |
| `registry_address` | String | Contract address of xAccountRegistry |
{% endtab %}
{% endtabs %}



## MigrateMsg

{% tabs %}
{% tab title="Rust" %}
```
 
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
