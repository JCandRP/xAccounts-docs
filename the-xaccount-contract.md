# The xAccount Contract

The xAccount contract acts as a transceiving point for incoming and outgoing mails.

{% tabs %}
{% tab title="CosmWasm" %}
```rust
#[cw_serde]
pub struct InstantiateMsg {
    pub x_account_registry: String,
    pub commanders: Vec<AccountInfo>,
}

#[cw_serde]
pub enum ExecuteMsg {
    SendMail { //mail originator
        outgoing_envelope: Envelope,
        outgoing_letter: Letter,
    },
    ReceiveMail { //mail responder
        vaa: Binary,
    },
    ReceiveMailResponse{ //mail originator processing mail responder's mail
        vaa: Binary
    },
    UpdateConfig {
        x_account_registry: String,
    },

    UpsertCommander{ //none to delete
        id: u64,
        account: Option<AccountInfo>,
    },

    UpsertSubordinate{ //none to delete, and factory is allowed to upsert non-none accounts
        id: u64,
        account: Option<AccountInfo>,
    },
}

#[cw_serde]
pub enum QueryMsg{
    Config{},

    ReadMail{ vaa: Binary},

    FetchMail{ mail_key: Binary},

    DeserializeMail{ serialized_mail: Binary},
}

#[cw_serde]
pub struct ConfigResponse{
    pub x_account_registry: String,
    pub commanders: Vec<AccountInfo>,
    pub subordinates: Vec<AccountInfo>,
}
```
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}
