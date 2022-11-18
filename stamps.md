# Stamps

Stamps are information filled in by the xAccount contract. They encode information about the mail itself.&#x20;



```rust
pub struct Stamp {
    id: MailId, // unique identifier of a mail 
    sender: AccountInfo, // sender of mail 
    emitter: AccountInfo, // VAA emitter - address of xAccount
    nonce: u32, 
    consistency_level: u8, 
}
```

| Key                | Type        | Description                            |
| ------------------ | ----------- | -------------------------------------- |
| id                 | MailId      | Unique identifier of a mail            |
| sender             | AccountInfo | Sender of mail                         |
| emitter            | AccountInfo | VAA emitter (address of xAccount used) |
| nonce              | u32         |                                        |
| consistency\_level | u8          |                                        |
