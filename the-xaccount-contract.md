# The xAccount Contract

The xAccount contract acts as a transceiving point for incoming and outgoing mails.&#x20;



```
pub struct Config {
	pub chain_id_here: u64, // chain id of the blockchain this contract resides on 
	pub x_account_code_id: u64, 
	pub chain_info: mapping[chain_id: u64] => ChainInfo, 
}

pub struct ChainInfo {
	pub wormhole_id: u64, 
	pub wormhole_core: String, 
	pub x_account_factory: String, 
	pub x_account_deployer: String 
}
```
