# The Registry Contract

The registry contract contains xAccounts deployment details on all supported chains.

{% tabs %}
{% tab title="CosmWasm" %}
```rust
#[cw_serde]
pub struct InstantiateMsg {
    pub wormhole_id_here: u64,
    pub wormhole_core_contract: String,
    pub factory_code_id: u64,
    pub x_account_code_id: u64,
    pub vm_id_here: u64,
}

#[cw_serde]
pub enum ExecuteMsg {
    UpdateConfig {
        wormhole_id_here: Option<u64>,
        owner: Option<String>,
    },

    //this should also dispatch a call to the factory to update its account deployer's commander/subordinate
    UpsertChainInfo {
        chain_info: ChainInfo,
    },
    UpdateFactory{
        factory_code_id: u64, //will also be upserted to the config
        migrate_msg: Binary,
    },
}

#[cw_serde]
pub enum QueryMsg {
    Config {},
    ChainInfo { 
        wormhole_id: Option<u64>
    },
    ChainInfos {
        start_after: Option<u64>,
        limit: Option<u64>,
    },
}

#[cw_serde]
pub struct ConfigResponse {
    pub wormhole_id_here: u64,
    pub wormhole_core_here: String,
    pub owner: String,
    pub factory_code_id: u64,
    pub x_account_code_id: u64,
}

#[cw_serde]
pub struct ChainInfo { 
    pub wormhole_id: u64, //2 for ethereum
    pub wormhole_core: String, 
    pub x_account_deployer: AccountInfo, 
    pub x_account_factory: AccountInfo,
    pub x_account_deployer_readable: String, // 0xd34db33f... format
    pub x_account_factory_readable: String, // 0xd34db33f... format
    pub vm_id: u64, // 1 for cosmwasm, 2 for evm, 3 for movevm
}
```
{% endtab %}

{% tab title="Second Tab" %}
```solidity
/**

The xAccount registry holds a list of all chain infos, and controls the factory contract

 */
interface IRegistry {

    /**

    structs

    */

    struct Config {
        //registry admin
        address owner;

        //wormhole_id of this contract's chain
        uint64 wormholeIdHere;

        //wormhole core contract of this contract's chain
        address wormholeCoreHere;

        //xAccount factory
        address factory;
    }

    struct ChainInfo{
        uint64 wormholeId;
        string wormholeCore;
        MailStructs.AccountInfo deployer;
        MailStructs.AccountInfo factory;
        string deployerReadable;
        string factoryReadable;
        uint64 vmId;
    }

    /**

    InstantiateMsg

    */

    constructor(uint64 wormholeIdHere, address wormholeCore );

    /**
    
    ExecuteMsgs

    */

    function updateConfig(Config calldata config) public;
    function upsertChainInfo(ChainInfo memory chainInfo) public;

    /**
    
    QueryMsgs
    
    */

    function getConfig() public view returns (Config memory);
    function getChainInfo(uint64 wormholeId) public view returns (ChainInfo memory);
    function getChainInfo() public view returns (ChainInfo memory);
    function getChainInfos() public view returns (ChainInfo[] memory);
}

```
{% endtab %}
{% endtabs %}

