# Letter

Letters represent the core body of a mail, comprised of the data being transferred and classifications on what to do with the data. Letters are assembled by the mail sender.

```rust
pub struct Letter {
    is_response_expected: u8, // 0 false, else true 
    is_executable: u8, // 0 false, else true
    x_data: Binary, 
}
```

| Key                                           | Type                        | Description                                                                                          |
| --------------------------------------------- | --------------------------- | ---------------------------------------------------------------------------------------------------- |
| <pre><code>is_response_expected
</code></pre> | <pre><code>u8
</code></pre> | If set as `true`, receiver should send back a response mail, otherwise mail marked as failed.        |
| <pre><code>is_executable
</code></pre>        | <pre><code>u8
</code></pre> | If set as `true`, letter contents should be executed post-receival, otherwise mail marked as failed. |
| `x_data`                                      | Binary                      | Base64-encoded JSON of message.                                                                      |

