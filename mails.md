# Mails

Mails represent an xChain request,

Mail = (Envelope) + (Letter) = (Envelope) +

```rust
pub struct Mail {
envelop: Envelope, 
letter: Binary, 
status: MailingStatus // status of mail. Can be one of Pending, Complete, or Failed

pub struct Mail {
    envelope: Envelope, 
    letter: Binary, 

    // Status of mail. Can be one of Pending, Complete, or Failed 
    status: MailingStatus, 

    // Mailing response. Filled in once response is received
    response: Option<RequestId> 
}



    wormhole_message: WormholeMessage, 
    /*
    Destination chain and address of request
    null for a general broadcast to all chains
    */
    destination_chain: Option<Vec<u8>>, 
    destination_address: Option<Vec<String>>, 

    /* 
    Optional caller designation - possible use for smart contracts to execute logic atomically right after VAA receival 
    null to allow relayers to finish receival on behalf of receiver
    */ 
    caller: Option<String>, 

    /* 
    Status of request. Can be one of pending, complete, or failed 
    */
    status: MailingStatus, 

    /*
    Request response. Filled in once response is received
    */
    response: Option<WormholeResponse> 
}
```
