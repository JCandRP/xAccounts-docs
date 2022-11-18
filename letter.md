# Letter

Letters represent the core body of a mail, comprised of the data being transferred and classifications on what to do with the data. Letters are assembled by the mail sender.&#x20;

```rust
pub struct Letter {
    msg_type: MsgType, 
    x_data: Binary, 
}
```

| Key       | Type    | Description                                 |
| --------- | ------- | ------------------------------------------- |
| msg\_type | MsgType | Defines how the message should be handled.  |
| x\_data   | Binary  | Base64-encoded JSON of message.             |



### `MsgType`

Defines what the mail recipient should do with the decoded message.&#x20;

```rust
pub enum MsgType {
    ExecuteMsg, 
    QueryMsg, 
    InstantiateMsg, 
    MigrateMsg, 
    XData 
}
```

| Key            | Description                                      |
| -------------- | ------------------------------------------------ |
| ExecuteMsg     | Orders a smart contract call.                    |
| QueryMsg       | Orders a smart contract query. Expects a reply.  |
| InstantiateMsg | Orders a smart contract instantiation.           |
| MigrateMsg     | Orders a smart contract migration.               |
| XData          | Simple transfer of data.                         |

