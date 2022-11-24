# Mail

Mails constitute a request made from chain A over to chain B. A mail consists of an envelope, a letter, and a stamp, each entailing details specifying the request.&#x20;

$$
\text{Mail} = \text{Envelope}+\text{Letter}+\text{Stamp}
$$

```rust
pub struct Mail {
    envelope: Envelope, 
    letter: Letter, 
    stamp: Option<Stamp>, 
    status: MailingStatus, 
    response: Option<MailId> 
}
```

| Key          | Type          | Description                                                                                                |
| ------------ | ------------- | ---------------------------------------------------------------------------------------------------------- |
| `envelope`   | Envelope      | Envelope of mail                                                                                           |
| `letter`     | Letter        | Letter of mail                                                                                             |
| `stamp`\*    | Stamp         | Stamp of mail                                                                                              |
| `status`     | MailingStatus | Status of mail. Can be one of Pending, Complete, or Failed.                                                |
| `response`\* | MailId        | Unique identifier of the mail who is the response of this mail. Filled in once response mail is received.  |

\* = optional

### `MailingStatus`

Defines which status the mail is currently in.&#x20;

```rust
pub enum MailingStatus {
    Pending, 
    Complete, 
    Failed
}
```

| Key        | Description                                                                                              |
| ---------- | -------------------------------------------------------------------------------------------------------- |
| `Pending`  | Mail is on its way to destination.                                                                       |
| `Complete` | Mail has either been sent out without expecting a response, or a successful response has been received.  |
| `Failed`   | Mail has either failed to be sent, or a failed response has been received.                               |



### `MailId`

Acts as a unique key for individual mails.&#x20;

```rust
pub struct MailId {
    pub chain_id: String, 
    pub sequence: u64, 
}
```

| Key        | Type   | Description                                    |
| ---------- | ------ | ---------------------------------------------- |
| `chain_id` | String | ID of blockchain (e.g. 1 for Ethereum mainnet) |
| `sequence` | u64    | Sequence number of mail's Wormhole VAA         |

