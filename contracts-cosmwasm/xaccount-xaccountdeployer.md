# xAccount / xAccountDeployer

## Contract State

### `Config`

Stores the contract configuration.&#x20;

{% tabs %}
{% tab title="Rust" %}
```rust
pub const CONFIG: Item<Config>
```

| Type   | Description                     |
| ------ | ------------------------------- |
| Config | xAccount contract configuration |

```rust
pub struct Config {
    pub chain_info_here: ChainInfo, 
    pub master: AccountInfo, 
}
```

| Key               | Type        | Description |
| ----------------- | ----------- | ----------- |
| `chain_info_here` | ChainInfo   |             |
| `master`          | AccountInfo |             |
{% endtab %}
{% endtabs %}



### `CompletedInstructions`

Stores the list of completed mails.&#x20;

{% tabs %}
{% tab title="Rust" %}
```rust
pub const COMPLETED_INSTRUCTIONS: Map<&[u8], bool>
```

| Type   | Description |
| ------ | ----------- |
| &\[u8] |             |
| bool   |             |
{% endtab %}
{% endtabs %}



### `Mailbox`

Stores the list of pending mails.&#x20;

{% tabs %}
{% tab title="Rust" %}
```rust
pub const MAILBOX: Map<&[u8], Vec<u8>>
```

| Type     | Description |
| -------- | ----------- |
| &\[u8]   |             |
| Vec\<u8> |             |
{% endtab %}
{% endtabs %}



## InstantiateMsg

{% tabs %}
{% tab title="Rust" %}
```rust
pub struct InstantiateMsg {
    pub chain_info_here: ChainInfo,
    pub master: AccountInfo,
}
```

| Key               | Type        | Description |
| ----------------- | ----------- | ----------- |
| `chain_info_here` | ChainInfo   |             |
| `master`          | AccountInfo |             |
{% endtab %}

{% tab title="JSON" %}
```json
{
  "chain_info_here": {}
  "master": {}
}
```

| Key               | Type        | Description |
| ----------------- | ----------- | ----------- |
| `chain_info_here` | ChainInfo   |             |
| `master`          | AccountInfo |             |
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
        master: AccountInfo, 
    }
}
```

| Key      | Type        | Description |
| -------- | ----------- | ----------- |
| `master` | AccountInfo |             |
{% endtab %}

{% tab title="JSON" %}
```json
{
  "update_config": {
    "master": {
    
    }
  }
}
```

| Key      | Type        | Description |
| -------- | ----------- | ----------- |
| `master` | AccountInfo |             |
{% endtab %}
{% endtabs %}



### `SendMail`

Sends out a new mail with the specified envelope and letter.&#x20;

{% tabs %}
{% tab title="Rust" %}
```rust
pub enum ExecuteMsg {
    SendMail {
        outgoing_envelope: Envelope, 
        outgoing_letter: Letter, 
    }
}
```

| Key                 | Type     | Description |
| ------------------- | -------- | ----------- |
| `outgoing_envelope` | Envelope |             |
| `outgoing_letter`   | Letter   |             |
{% endtab %}

{% tab title="JSON" %}
```json
{
  "send_mail": {
    "outgoing_envelope": {}, 
    "outgoing_letter": {}
  }
}
```

| Key                 | Type     | Description |
| ------------------- | -------- | ----------- |
| `outgoing_envelope` | Envelope |             |
| `outgoing_letter`   | Letter   |             |
{% endtab %}
{% endtabs %}



### `ReceiveMail`

Receives an inbound mail.&#x20;

{% tabs %}
{% tab title="Rust" %}
```rust
pub enum ExecuteMsg {
    ReceiveMail {
        vaa: Binary, 
    }
}
```

| Key   | Type   | Description          |
| ----- | ------ | -------------------- |
| `vaa` | Binary | Wormhole VAA of mail |
{% endtab %}

{% tab title="JSON" %}
```json
{
  "vaa": "" 
}
```

| Key   | Type   | Description          |
| ----- | ------ | -------------------- |
| `vaa` | Binary | Wormhole VAA of mail |
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
pub struct Config {
    pub chain_info_here: ChainInfo, 
    pub master: AccountInfo, 
}
```

| Key               | Type        | Description |
| ----------------- | ----------- | ----------- |
| `chain_info_here` | ChainInfo   |             |
| `master`          | AccountInfo |             |
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
  "chain_info_here": {}
  "master": {}
}
```

| Key               | Type        | Description |
| ----------------- | ----------- | ----------- |
| `chain_info_here` | ChainInfo   |             |
| `master`          | AccountInfo |             |
{% endtab %}
{% endtabs %}



### `ReadMail`

{% tabs %}
{% tab title="Rust" %}
#### Request

```rust
pub enum QueryMsg {
    ReadMail {
        vaa: Binary, 
    }
}
```

| Key   | Type   | Description |
| ----- | ------ | ----------- |
| `vaa` | Binary |             |

#### Response

```rust
// Some code
```

| Key | Type | Description |
| --- | ---- | ----------- |
|     |      |             |
|     |      |             |
|     |      |             |
{% endtab %}

{% tab title="JSON" %}
#### Request

```json
{
  "read_mail": {
    "vaa": ""
  }
}
```

| Key   | Type   | Description |
| ----- | ------ | ----------- |
| `vaa` | Binary |             |

#### Response

```json
```

| Key | Type | Description |
| --- | ---- | ----------- |
|     |      |             |
|     |      |             |
|     |      |             |
{% endtab %}
{% endtabs %}



## MigrateMsg

{% tabs %}
{% tab title="Rust" %}
```rust
pub struct MigrateMsg {}
```

| Key | Type | Description |
| --- | ---- | ----------- |
|     |      |             |
{% endtab %}

{% tab title="JSON" %}
```json
```

| Key | Type | Description |
| --- | ---- | ----------- |
|     |      |             |
{% endtab %}
{% endtabs %}



