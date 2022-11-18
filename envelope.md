# Envelope

Envelopes encapsulate the characteristics of a mail, used by the mail receiver to determine how to handle the mail post-receival. Envelopes are assembled by the mail sender.&#x20;

```rust
pub struct Envelope {
    destination_chain: Option<Vec<u8>>, 
    destination_address: Option<Vec<String>>, 

    is_response_expected: bool, 
    is_executable: bool, 
    execution_dependency: Option<MailId>, 

    opener: Option<String>, 

    response_of: Option<MailId> 
}
```

| Key                     | Type         | Description                                                                                                                                                                                                                         |
| ----------------------- | ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| destination\_chain\*    | Vec\<u8>     | Destination chain of mail. `null` for a multicast to all supported chains.                                                                                                                                                          |
| destination\_address\*  | Vec\<String> | Destination address of mail. `null` for a multicast to all addresses of a chain.                                                                                                                                                    |
| is\_response\_expected  | bool         | If set as `true`, receiver should send back a response mail, otherwise mail marked as failed.                                                                                                                                       |
| is\_executable          | bool         | If set as `true`, letter contents should be executed post-receival, otherwise mail marked as failed.                                                                                                                                |
| execution\_dependency\* | MailId       | ID of mail that should be executed prior to this mail's execution.                                                                                                                                                                  |
| opener\*                | String       | <p>Address of designated mail opener. <code>null</code> to allow anyone (including relayers) to open mail on behalf of receiver. <br><br>Possible use for contracts to include mail opening within execution of certain logic. </p> |
| response\_of\*          | MailId       | ID of mail that triggered this mail. Filled if mail is a response to a previous mail.                                                                                                                                               |

\* = optional
