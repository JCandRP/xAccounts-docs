# Envelope

Envelopes encapsulate the characteristics of a mail, used by the mail receiver to determine how to handle the mail post-receival. Envelopes are assembled by the mail sender.

```rust
pub struct Envelope {
    destination: AccountInfo, // null for multicasting next version
    
    //execution_dependency: Option<MailId>, # next version 

    opener: Option<AccountInfo>, 
    response_of: Option<MailId> 
}
```



| Key                    | Type                 | Description                                                                                                                                                                                                                               |
| ---------------------- | -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| destination            | AccountInfo          | Destination account details of mail. `null` for a multicast to all supported chains.                                                                                                                                                      |
| `execution_dependency` | Option\<MailId>      | ID of mail that should be executed prior to this mail's execution.                                                                                                                                                                        |
| `opener`               | Option\<AccountInfo> | <p>Address details of designated mail opener. <code>null</code> to allow anyone (including relayers) to open mail on behalf of receiver.<br><br>Possible use for contracts to include mail opening within execution of certain logic.</p> |
| `response_of`          | Option\<MailId>      | ID of mail that triggered this mail. Filled if mail is a response to a previous mail.                                                                                                                                                     |
