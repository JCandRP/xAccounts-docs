# Letters

Letters

```rust
pub struct Letter {
    // values optional if used for execution dependency settings 
    message: Option<Message>, 
    emitter: Option<AccountInfo>, 
    sequence: Option<u64>, 
    is_response_expected: Option<bool>, // 1: receiver should send back response, otherwise abort 
    is_executable: Option<bool>, // 1: payload must be executed post-receival, otherwise abort 
    execution_dependency: Option<WormholeMessage>
}
```
