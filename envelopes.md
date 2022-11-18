# Envelopes

Envelopes encapsulate details th

that are assemblable prior to issuing a letter.&#x20;

```rust
pub struct Envelope {
    destination_chain: Option<Vec<u8>>, // destination chain. null for a multicast to all chains
    destination_address: Option<Vec<String>>, // destination address. null for a multicast to all addresses of a chain 

    is_response_expected: bool, // 1: receiver should send back a response, otherwise abort 
    is_executable: bool, // 1: payload must be executed post-receival, otherwise abort 
    execution_dependency: Option<MailId>, 

    /* 
    Optional opener designation - possible use for smart contracts to execute logic atomically right after VAA receival 
    null to allow relayers to open mails on behalf of the receiver
    */ 
    opener: Option<String>, 

    /*
    filled if mail is a response to a previous mail. 
    Id of of mail that triggered this response 
    */
    response_of: Option<MailId> 
}



    // values optional if used for execution dependency settings 
    message: Option<Message>, 
    emitter: Option<AccountInfo>, 
    sequence: Option<u64>, 
    is_response_expected: Option<bool>, // 1: receiver should send back response, otherwise abort 
    is_executable: Option<bool>, // 1: payload must be executed post-receival, otherwise abort 
    execution_dependency: Option<WormholeMessage>
}
```

| Key                    | Type | Description |
| ---------------------- | ---- | ----------- |
| destination\_chain     |      |             |
| destination\_address   |      |             |
| is\_response\_expected |      |             |
| is\_executable         |      |             |
| execution\_dependency  |      |             |
| opener                 |      |             |
| response\_of           |      |             |
|                        |      |             |
|                        |      |             |
