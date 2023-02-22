# Mail

Mails constitute a request made from chain A over to chain B. A mail consists of an envelope, a letter, and a stamp, each entailing details specifying the request.&#x20;

$$
\text{Mail} = \text{Envelope}+\text{Letter}+\text{Stamp}
$$

### Mail Lifecycle

The lifecycle of a mail can be compared to the lifecycle of a real-world post office mail.&#x20;

1. The mail sender prepares an **envelope** specifying the letter details such as the destination, package type, who has the authority to open the envelope, etc.&#x20;
2. A **letter** encompassing data or execution instructions is packaged in the envelope and sent to a xAccount (analogous to a post office).&#x20;
3. The xAccount **stamps** the enclosed envelope with the mail sender and xAccount's credentials, which then the mail is then reformatted to a structure transmissible through a messaging bridge.&#x20;



### Structure

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
| `stamp`\*    | Stamp         | Stamp of mail. Filled in after stamped by xAccount.                                                        |
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

Acts as a unique identifier key for individual mails (there can only exist 1 unique VAA sequence number per chain).&#x20;

```rust
pub struct MailId {
    pub wormhole_id: u64, 
    pub sequence: u64, 
}
```

| Key        | Type | Description                                                   |
| ---------- | ---- | ------------------------------------------------------------- |
| `chain_id` | u64  | Wormhole chain ID of blockchain (e.g. 2 for Ethereum mainnet) |
| `sequence` | u64  | Sequence number of mail's Wormhole VAA                        |
