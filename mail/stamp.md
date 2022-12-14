# Stamp

Stamps are information filled in by the xAccount contract and thus not mutable by the mail sender. They encode information about the mail sender and which xAccount was responsible for broadcasting this mail.&#x20;

```rust
pub struct Stamp {
    id: MailId, 
    sender: AccountInfo, 
    emitter: AccountInfo, 
    nonce: u32, 
    consistency_level: u8, 
}
```

| Key                 | Type        | Description                                                                             |
| ------------------- | ----------- | --------------------------------------------------------------------------------------- |
| `id`                | MailId      | Unique identifier of a mail.                                                            |
| `sender`            | AccountInfo | Sender of mail.                                                                         |
| `emitter`           | AccountInfo | VAA emitter (address of xAccount used).                                                 |
| `nonce`             | u32         | Used for batch VAAs; messages can be created with the same nonce to group them.         |
| `consistency_level` | u8          | Used by Wormhole bridge. What finality level was reached before emitting this message.  |
