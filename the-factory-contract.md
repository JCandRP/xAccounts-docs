# The Factory Contract

The factory contract creates new xAccounts using... its own xAccount! The genesis xAccount is a special-purposed contract for the factories to communicate over wormhole.&#x20;

<figure><img src=".gitbook/assets/Screenshot from 2023-02-22 19-49-30.png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="CosmWasm" %}
```rust
#[cw_serde]
pub struct InstantiateMsg {
  pub registry_address: String,
  pub x_account_code_id: u64,
}

#[cw_serde]
pub enum ExecuteMsg{
  CreateXAccounts{
    chain_ids: Option<Vec<u64>>, //only deploy to factory's chain if empty
    initial_commander: AccountInfo
  },

  OpenMail{ 
    vaa: Binary,
  },

  UpsertDeployerCommander{
    id: u64,
    account: Option<AccountInfo>,
  },

  UpsertDeployerSubordinate{
    id: u64,
    account: Option<AccountInfo>,
  },
}

#[cw_serde]
pub enum QueryMsg{
  Config{},
}
```
{% endtab %}

{% tab title="Solidity" %}

{% endtab %}
{% endtabs %}
