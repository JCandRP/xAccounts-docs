# Envelopes

```rust
pub struct Envelope {

// --- Filled in by xAccount ---
id: Option<MailId>, // unique identifier of a mail
sender: Option<AccountInfo>, // mail sender
emitter: Option<AccountInfo>, // VAA emitter
nonce: Option<u32>, 
consistency_level: Option<u8>, 

// --- Filled in by sender ---
destination_chain: Option<Vec<u8>>, // destination chain. null for a multicast to all chains
destination_address: Option<Vec<String>>, // destination address. null for a multicast to all addresses of a chain 

is_response_expected: bool, // 1: receiver should send back a response, otherwise abort 
is_executable: bool, // 1: payload must be executed post-receival, otherwise abort 
execution_dependency: Option<MailId>, 

/* 
Optional caller designation - possible use for smart contracts to execute logic atomically right after VAA receival 
null to allow relayers to finish receival on behalf of receiver
*/ 
caller: Option<String>, 

/*
filled if request is a response of a previous request. 
Sequence of VAA that triggered this response 
*/
response_of: Option<MailId> 
}
```
