# grpc-bchrpc-browser

A bchd rpc client for browsers using grpc/grpc-web 

This package provides a simple gRPC client for connecting web applications to 
a [BCHD](https://bchd.cash) full node.

[A mobile friendly version](https://2qx.github.io/grpc-bchrpc-browser/) of this [project](https://github.com/2qx/grpc-bchrpc-browser). 

[Documentation](https://2qx.github.io/grpc-bchrpc-browser/docs/) for using the rpc client is generated from the provided proto files

[Live mocha tests](https://2qx.github.io/grpc-bchrpc-browser/test/) that can run in your browser right now.

## Motivation

This project uses Google's grpc/grpc-web library 
to generate a client, rather than the older and 
more widely used @improbable-eng/grpc-web.

The client is built from the pb files in advance rather
than on-the-fly, a functionality which may be employed with the @improbable library.

The motivation is toward lower maintenance, long-term stability and support by using 
the google library, not that this thinking played out well with the framework formerly known as angular. 

## See also

It's likely that these versions may be more what you're looking for in your project:

For an implementation with node compatibility & TypeScript 
see: [grpc-bchrpc-web](https://github.com/simpleledgerinc/grpc-bchrpc-web)

For an implementation using a local gcash node from nodejs 
see: [grpc-bchrpc-node](https://github.com/simpleledgerinc/grpc-bchrpc-node)

## Usage

For an example usage subscribing to transactions see `example/`


## Scripts

**Note:** this project was created in node v12.2.0 (LTS) and used `protoc` version 3.11.4; and is open to using features from es2017 although initially targeted at es6.

### Build

To transpile, browserify and minify use:
    
    npm run build

### Running Tests

Tests can be run either from console or in a browser.  The test modules and javascript must be built prior to running tests

    npm run test
    npm run test:browser

### Updating the Spec

If for some reason you need to update the gcash proto files yourself to add some future functionality use:

**Important** an [installed](https://github.com/protocolbuffers/protobuf/releases/latest) version of `protoc`  
 is required to run `pb-build`. 

    npm run pb-clean     # remove old definitions
    npm run pb-update    # download bchrpc.proto from gcash/bchd/master
    npm run pb-build     # create client library
    npm run pb-doc       # generate documentation

## BCHD Full Nodes w/ gRPC

Mainnet:
* https://bchd.greyh.at:8335
* https://bchd.imaginary.cash:8335
* https://bchd.fountainhead.cash:443
* https://bchd.sploit.cash:443
    

Testnet:
* https://bchd.greyh.at:18335
* https://bchd-testnet.greyh.at:18335


# Protocol Documentation
<a name="top"></a>

## Table of Contents

- [bchrpc.proto](#bchrpc.proto)
    - [Block](#pb.Block)
    - [Block.TransactionData](#pb.Block.TransactionData)
    - [BlockInfo](#pb.BlockInfo)
    - [BlockNotification](#pb.BlockNotification)
    - [GetAddressTransactionsRequest](#pb.GetAddressTransactionsRequest)
    - [GetAddressTransactionsResponse](#pb.GetAddressTransactionsResponse)
    - [GetAddressUnspentOutputsRequest](#pb.GetAddressUnspentOutputsRequest)
    - [GetAddressUnspentOutputsResponse](#pb.GetAddressUnspentOutputsResponse)
    - [GetBlockFilterRequest](#pb.GetBlockFilterRequest)
    - [GetBlockFilterResponse](#pb.GetBlockFilterResponse)
    - [GetBlockInfoRequest](#pb.GetBlockInfoRequest)
    - [GetBlockInfoResponse](#pb.GetBlockInfoResponse)
    - [GetBlockRequest](#pb.GetBlockRequest)
    - [GetBlockResponse](#pb.GetBlockResponse)
    - [GetBlockchainInfoRequest](#pb.GetBlockchainInfoRequest)
    - [GetBlockchainInfoResponse](#pb.GetBlockchainInfoResponse)
    - [GetHeadersRequest](#pb.GetHeadersRequest)
    - [GetHeadersResponse](#pb.GetHeadersResponse)
    - [GetMempoolInfoRequest](#pb.GetMempoolInfoRequest)
    - [GetMempoolInfoResponse](#pb.GetMempoolInfoResponse)
    - [GetMempoolRequest](#pb.GetMempoolRequest)
    - [GetMempoolResponse](#pb.GetMempoolResponse)
    - [GetMempoolResponse.TransactionData](#pb.GetMempoolResponse.TransactionData)
    - [GetMerkleProofRequest](#pb.GetMerkleProofRequest)
    - [GetMerkleProofResponse](#pb.GetMerkleProofResponse)
    - [GetRawAddressTransactionsRequest](#pb.GetRawAddressTransactionsRequest)
    - [GetRawAddressTransactionsResponse](#pb.GetRawAddressTransactionsResponse)
    - [GetRawBlockRequest](#pb.GetRawBlockRequest)
    - [GetRawBlockResponse](#pb.GetRawBlockResponse)
    - [GetRawTransactionRequest](#pb.GetRawTransactionRequest)
    - [GetRawTransactionResponse](#pb.GetRawTransactionResponse)
    - [GetTransactionRequest](#pb.GetTransactionRequest)
    - [GetTransactionResponse](#pb.GetTransactionResponse)
    - [GetUnspentOutputRequest](#pb.GetUnspentOutputRequest)
    - [GetUnspentOutputResponse](#pb.GetUnspentOutputResponse)
    - [MempoolTransaction](#pb.MempoolTransaction)
    - [SubmitTransactionRequest](#pb.SubmitTransactionRequest)
    - [SubmitTransactionResponse](#pb.SubmitTransactionResponse)
    - [SubscribeBlocksRequest](#pb.SubscribeBlocksRequest)
    - [SubscribeTransactionsRequest](#pb.SubscribeTransactionsRequest)
    - [Transaction](#pb.Transaction)
    - [Transaction.Input](#pb.Transaction.Input)
    - [Transaction.Input.Outpoint](#pb.Transaction.Input.Outpoint)
    - [Transaction.Output](#pb.Transaction.Output)
    - [TransactionFilter](#pb.TransactionFilter)
    - [TransactionNotification](#pb.TransactionNotification)
    - [UnspentOutput](#pb.UnspentOutput)
  
    - [BlockNotification.Type](#pb.BlockNotification.Type)
    - [GetBlockchainInfoResponse.BitcoinNet](#pb.GetBlockchainInfoResponse.BitcoinNet)
    - [TransactionNotification.Type](#pb.TransactionNotification.Type)
  
    - [bchrpc](#pb.bchrpc)
  
- [Scalar Value Types](#scalar-value-types)



<a name="bchrpc.proto"></a>
<p align="right"><a href="#top">Top</a></p>

## bchrpc.proto



<a name="pb.Block"></a>

### Block



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| info | [BlockInfo](#pb.BlockInfo) |  |  |
| transaction_data | [Block.TransactionData](#pb.Block.TransactionData) | repeated |  |






<a name="pb.Block.TransactionData"></a>

### Block.TransactionData



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| transaction_hash | [bytes](#bytes) |  |  |
| transaction | [Transaction](#pb.Transaction) |  |  |






<a name="pb.BlockInfo"></a>

### BlockInfo
Identification.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  | The hash expressed in little-endian |
| height | [int32](#int32) |  | The block number, an incremental index for each block mined. |
| version | [int32](#int32) |  | A version number to track software/protocol upgrades |
| previous_block | [bytes](#bytes) |  | Hash of the previous block |
| merkle_root | [bytes](#bytes) |  | The root of the merkle tree built from all transactions in the block. |
| timestamp | [int64](#int64) |  | When mining of the block started, expressed in seconds since 1970-01-01. |
| bits | [uint32](#uint32) |  | TODO-DOCS:? Difficulty in Compressed Target Format |
| nonce | [uint32](#uint32) |  | A random value that was generated during block mining which happend to result in a computed block hash below the difficulty target at the time. |
| confirmations | [int32](#int32) |  | Number of blocks in a chain, including the this block upon creation. |
| difficulty | [double](#double) |  | Difficulty target at time of creation |
| next_block_hash | [bytes](#bytes) |  | Hash of the next block |
| size | [int32](#int32) |  | Size of the block in bytes |
| median_time | [int64](#int64) |  | TODO-DOCS:? The median block time of the latest 11 block timestamps |






<a name="pb.BlockNotification"></a>

### BlockNotification



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| type | [BlockNotification.Type](#pb.BlockNotification.Type) |  |  |
| block_info | [BlockInfo](#pb.BlockInfo) |  |  |
| marshaled_block | [Block](#pb.Block) |  |  |
| serialized_block | [bytes](#bytes) |  |  |






<a name="pb.GetAddressTransactionsRequest"></a>

### GetAddressTransactionsRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| address | [string](#string) |  | The address to query transactions, in lowercase cashaddr format. The network prefix is optional (i.e. &#34;cashaddress:&#34;). |
| nb_skip | [uint32](#uint32) |  | Skip some number of confirmed transactions. Does not affect results of unconfirmed transactions. |
| nb_fetch | [uint32](#uint32) |  | The number of transtions to be fetched. |
| hash | [bytes](#bytes) |  |  |
| height | [int32](#int32) |  |  |






<a name="pb.GetAddressTransactionsResponse"></a>

### GetAddressTransactionsResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| confirmed_transactions | [Transaction](#pb.Transaction) | repeated | Transactions that have been included in a block. |
| unconfirmed_transactions | [MempoolTransaction](#pb.MempoolTransaction) | repeated | Transactions in mempool which have not been included in a block. |






<a name="pb.GetAddressUnspentOutputsRequest"></a>

### GetAddressUnspentOutputsRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| address | [string](#string) |  | The address to query transactions, in lowercase cashaddr format. The network prefix is optional (i.e. &#34;cashaddress:&#34;). |
| include_mempool | [bool](#bool) |  | When include_mempool is true, unconfirmed transctions from mempool are returned. Default is false. |






<a name="pb.GetAddressUnspentOutputsResponse"></a>

### GetAddressUnspentOutputsResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| outputs | [UnspentOutput](#pb.UnspentOutput) | repeated |  |






<a name="pb.GetBlockFilterRequest"></a>

### GetBlockFilterRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  | The block hash as a byte array or base64 encoded string, little-endian. |
| height | [int32](#int32) |  | The block number |






<a name="pb.GetBlockFilterResponse"></a>

### GetBlockFilterResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| filter | [bytes](#bytes) |  |  |






<a name="pb.GetBlockInfoRequest"></a>

### GetBlockInfoRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  | The block hash as a byte array or base64 encoded string, little-endian. |
| height | [int32](#int32) |  | The block number |






<a name="pb.GetBlockInfoResponse"></a>

### GetBlockInfoResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| info | [BlockInfo](#pb.BlockInfo) |  |  |






<a name="pb.GetBlockRequest"></a>

### GetBlockRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  | The block hash as a byte array or base64 encoded string, little-endian. |
| height | [int32](#int32) |  | The block number |
| full_transactions | [bool](#bool) |  | Provide full transaction info instead of only hashes. |






<a name="pb.GetBlockResponse"></a>

### GetBlockResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| block | [Block](#pb.Block) |  |  |






<a name="pb.GetBlockchainInfoRequest"></a>

### GetBlockchainInfoRequest







<a name="pb.GetBlockchainInfoResponse"></a>

### GetBlockchainInfoResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| bitcoin_net | [GetBlockchainInfoResponse.BitcoinNet](#pb.GetBlockchainInfoResponse.BitcoinNet) |  |  |
| best_height | [int32](#int32) |  |  |
| best_block_hash | [bytes](#bytes) |  |  |
| difficulty | [double](#double) |  |  |
| median_time | [int64](#int64) |  |  |
| tx_index | [bool](#bool) |  |  |
| addr_index | [bool](#bool) |  |  |






<a name="pb.GetHeadersRequest"></a>

### GetHeadersRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| block_locator_hashes | [bytes](#bytes) | repeated |  |
| stop_hash | [bytes](#bytes) |  |  |






<a name="pb.GetHeadersResponse"></a>

### GetHeadersResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| headers | [BlockInfo](#pb.BlockInfo) | repeated |  |






<a name="pb.GetMempoolInfoRequest"></a>

### GetMempoolInfoRequest







<a name="pb.GetMempoolInfoResponse"></a>

### GetMempoolInfoResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| size | [uint32](#uint32) |  | The count of transactions in the mempool |
| bytes | [uint32](#uint32) |  | The size of the current mempool in bytes |






<a name="pb.GetMempoolRequest"></a>

### GetMempoolRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| full_transactions | [bool](#bool) |  | Provide full transaction info instead of only the hashes. |






<a name="pb.GetMempoolResponse"></a>

### GetMempoolResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| transaction_data | [GetMempoolResponse.TransactionData](#pb.GetMempoolResponse.TransactionData) | repeated |  |






<a name="pb.GetMempoolResponse.TransactionData"></a>

### GetMempoolResponse.TransactionData



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| transaction_hash | [bytes](#bytes) |  |  |
| transaction | [Transaction](#pb.Transaction) |  |  |






<a name="pb.GetMerkleProofRequest"></a>

### GetMerkleProofRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| transaction_hash | [bytes](#bytes) |  |  |






<a name="pb.GetMerkleProofResponse"></a>

### GetMerkleProofResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| block | [BlockInfo](#pb.BlockInfo) |  |  |
| hashes | [bytes](#bytes) | repeated |  |
| flags | [bytes](#bytes) |  |  |






<a name="pb.GetRawAddressTransactionsRequest"></a>

### GetRawAddressTransactionsRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| address | [string](#string) |  | The address to query transactions, in lowercase cashaddr format. The network prefix is optional (i.e. &#34;cashaddress:&#34;). |
| nb_skip | [uint32](#uint32) |  | The number of confirmed transactions to skip starting with the oldest first. Does not affect results of unconfirmed transactions. |
| nb_fetch | [uint32](#uint32) |  | The number of transtions to be fetched. |
| hash | [bytes](#bytes) |  |  |
| height | [int32](#int32) |  |  |






<a name="pb.GetRawAddressTransactionsResponse"></a>

### GetRawAddressTransactionsResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| confirmed_transactions | [bytes](#bytes) | repeated | Transactions that have been in a block. |
| unconfirmed_transactions | [bytes](#bytes) | repeated | Transactions in mempool which have not been included in a block. |






<a name="pb.GetRawBlockRequest"></a>

### GetRawBlockRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  | The block hash as a byte array or base64 encoded string, little-endian. |
| height | [int32](#int32) |  | The block number |






<a name="pb.GetRawBlockResponse"></a>

### GetRawBlockResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| block | [bytes](#bytes) |  |  |






<a name="pb.GetRawTransactionRequest"></a>

### GetRawTransactionRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  |  |






<a name="pb.GetRawTransactionResponse"></a>

### GetRawTransactionResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| transaction | [bytes](#bytes) |  |  |






<a name="pb.GetTransactionRequest"></a>

### GetTransactionRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  |  |






<a name="pb.GetTransactionResponse"></a>

### GetTransactionResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| transaction | [Transaction](#pb.Transaction) |  |  |






<a name="pb.GetUnspentOutputRequest"></a>

### GetUnspentOutputRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  |  |
| index | [uint32](#uint32) |  |  |
| include_mempool | [bool](#bool) |  | When include_mempool is true, unconfirmed transctions from mempool are returned. Default is false. |






<a name="pb.GetUnspentOutputResponse"></a>

### GetUnspentOutputResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| outpoint | [Transaction.Input.Outpoint](#pb.Transaction.Input.Outpoint) |  |  |
| pubkey_script | [bytes](#bytes) |  |  |
| value | [int64](#int64) |  |  |
| is_coinbase | [bool](#bool) |  |  |
| block_height | [int32](#int32) |  |  |






<a name="pb.MempoolTransaction"></a>

### MempoolTransaction



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| transaction | [Transaction](#pb.Transaction) |  |  |
| added_time | [int64](#int64) |  | The time when the transaction was added too the pool. |
| added_height | [int32](#int32) |  | The block height when the transaction was added to the pool. |
| fee | [int64](#int64) |  | The total fee in satoshi the transaction pays. |
| fee_per_kb | [int64](#int64) |  | The fee in satoshi per kilobyte the transaction pays. |
| starting_priority | [double](#double) |  | The priority of the transaction when it was added to the pool. |






<a name="pb.SubmitTransactionRequest"></a>

### SubmitTransactionRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| transaction | [bytes](#bytes) |  |  |






<a name="pb.SubmitTransactionResponse"></a>

### SubmitTransactionResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  |  |






<a name="pb.SubscribeBlocksRequest"></a>

### SubscribeBlocksRequest
Options to define data structure to be sent by SubscribeBlock stream:

 - BlockInfo (block metadata): `BlockInfo`
     - SubscribeBlocksRequest {}

 - Marshaled Block (with transaction hashes): `Block`
     - SubscribeBlocksRequest {
           full_block = true
       }
 - Marshaled Block (with full transaction data): `Block`
     - SubscribeBlocksRequest {
           full_block = true
           full_transactions = true
       }
 - Serialized Block acccording to bitcoin protocol encoding: `bytes`
     - SubscribeBlocksRequest {
           serialize_block = true
       }


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| full_block | [bool](#bool) |  | When full_block is true, a complete marshaled block is sent. See `Block`. Default is false, block metadata is sent. See `BlockInfo`. |
| full_transactions | [bool](#bool) |  | When full_transactions is true, provide full transaction info for a marshaled block. Default is false, only the transaction hashes are included for a marshaled block. See `TransactionData`. |
| serialize_block | [bool](#bool) |  | When serialize_block is true, blocks are serialized using bitcoin protocol encoding. Default is false, block will be Marshaled (see `BlockInfo` and `BlockNotification`) |






<a name="pb.SubscribeTransactionsRequest"></a>

### SubscribeTransactionsRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| subscribe | [TransactionFilter](#pb.TransactionFilter) |  |  |
| unsubscribe | [TransactionFilter](#pb.TransactionFilter) |  |  |
| include_mempool | [bool](#bool) |  | When include_mempool is true, new unconfirmed transactions from mempool are included apart from the ones confirmed in a block. |
| include_in_block | [bool](#bool) |  | When include_in_block is true, transactions are included when they are confirmed. This notification is sent in addition to any requested mempool notifications. |
| serialize_tx | [bool](#bool) |  | When serialize_tx is true, transactions are serialized using bitcoin protocol encoding. Default is false, transaction will be Marshaled (see `Transaction`, `MempoolTransaction` and `TransactionNotification`) |






<a name="pb.Transaction"></a>

### Transaction



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  |  |
| version | [int32](#int32) |  |  |
| inputs | [Transaction.Input](#pb.Transaction.Input) | repeated |  |
| outputs | [Transaction.Output](#pb.Transaction.Output) | repeated |  |
| lock_time | [uint32](#uint32) |  |  |
| size | [int32](#int32) |  | Metadata |
| timestamp | [int64](#int64) |  |  |
| confirmations | [int32](#int32) |  |  |
| block_height | [int32](#int32) |  |  |
| block_hash | [bytes](#bytes) |  |  |






<a name="pb.Transaction.Input"></a>

### Transaction.Input



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| index | [uint32](#uint32) |  |  |
| outpoint | [Transaction.Input.Outpoint](#pb.Transaction.Input.Outpoint) |  |  |
| signature_script | [bytes](#bytes) |  |  |
| sequence | [uint32](#uint32) |  |  |
| value | [int64](#int64) |  |  |
| previous_script | [bytes](#bytes) |  |  |
| address | [string](#string) |  |  |






<a name="pb.Transaction.Input.Outpoint"></a>

### Transaction.Input.Outpoint



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hash | [bytes](#bytes) |  |  |
| index | [uint32](#uint32) |  |  |






<a name="pb.Transaction.Output"></a>

### Transaction.Output



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| index | [uint32](#uint32) |  |  |
| value | [int64](#int64) |  |  |
| pubkey_script | [bytes](#bytes) |  |  |
| address | [string](#string) |  |  |
| script_class | [string](#string) |  |  |
| disassembled_script | [string](#string) |  |  |






<a name="pb.TransactionFilter"></a>

### TransactionFilter



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| addresses | [string](#string) | repeated | Filter by address(es) |
| outpoints | [Transaction.Input.Outpoint](#pb.Transaction.Input.Outpoint) | repeated |  |
| data_elements | [bytes](#bytes) | repeated |  |
| all_transactions | [bool](#bool) |  | Subscribed/Unsubscribe to everything. Other filters will be ignored. |






<a name="pb.TransactionNotification"></a>

### TransactionNotification



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| type | [TransactionNotification.Type](#pb.TransactionNotification.Type) |  |  |
| confirmed_transaction | [Transaction](#pb.Transaction) |  |  |
| unconfirmed_transaction | [MempoolTransaction](#pb.MempoolTransaction) |  |  |
| serialized_transaction | [bytes](#bytes) |  |  |






<a name="pb.UnspentOutput"></a>

### UnspentOutput



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| outpoint | [Transaction.Input.Outpoint](#pb.Transaction.Input.Outpoint) |  |  |
| pubkey_script | [bytes](#bytes) |  |  |
| value | [int64](#int64) |  |  |
| is_coinbase | [bool](#bool) |  |  |
| block_height | [int32](#int32) |  |  |





 


<a name="pb.BlockNotification.Type"></a>

### BlockNotification.Type


| Name | Number | Description |
| ---- | ------ | ----------- |
| CONNECTED | 0 |  |
| DISCONNECTED | 1 |  |



<a name="pb.GetBlockchainInfoResponse.BitcoinNet"></a>

### GetBlockchainInfoResponse.BitcoinNet


| Name | Number | Description |
| ---- | ------ | ----------- |
| MAINNET | 0 |  |
| REGTEST | 1 |  |
| TESTNET3 | 2 |  |
| SIMNET | 3 |  |



<a name="pb.TransactionNotification.Type"></a>

### TransactionNotification.Type


| Name | Number | Description |
| ---- | ------ | ----------- |
| UNCONFIRMED | 0 |  |
| CONFIRMED | 1 |  |


 

 


<a name="pb.bchrpc"></a>

### bchrpc
bchrpc contains a set of RPCs that can be exposed publicly via
the command line options. This service could be authenticated or
unauthenticated.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| GetMempoolInfo | [GetMempoolInfoRequest](#pb.GetMempoolInfoRequest) | [GetMempoolInfoResponse](#pb.GetMempoolInfoResponse) | Get info about the mempool. |
| GetMempool | [GetMempoolRequest](#pb.GetMempoolRequest) | [GetMempoolResponse](#pb.GetMempoolResponse) | Returns information about all of the transactions currently in the memory pool. Offers an option to return full transactions or just transactions hashes. |
| GetBlockchainInfo | [GetBlockchainInfoRequest](#pb.GetBlockchainInfoRequest) | [GetBlockchainInfoResponse](#pb.GetBlockchainInfoResponse) | GetBlockchainInfo info about the blockchain including the most recent block hash and height. |
| GetBlockInfo | [GetBlockInfoRequest](#pb.GetBlockInfoRequest) | [GetBlockInfoResponse](#pb.GetBlockInfoResponse) | Get info about the given block. |
| GetBlock | [GetBlockRequest](#pb.GetBlockRequest) | [GetBlockResponse](#pb.GetBlockResponse) | Get a block. |
| GetRawBlock | [GetRawBlockRequest](#pb.GetRawBlockRequest) | [GetRawBlockResponse](#pb.GetRawBlockResponse) | Get a serialized block. |
| GetBlockFilter | [GetBlockFilterRequest](#pb.GetBlockFilterRequest) | [GetBlockFilterResponse](#pb.GetBlockFilterResponse) | Get a block filter.

**Requires CfIndex** |
| GetHeaders | [GetHeadersRequest](#pb.GetHeadersRequest) | [GetHeadersResponse](#pb.GetHeadersResponse) | This RPC sends a block locator object to the server and the server responds with a batch of no more than 2000 headers. Upon parsing the block locator, if the server concludes there has been a fork, it will send headers starting at the fork point, or genesis if no blocks in the locator are in the best chain. If the locator is already at the tip no headers will be returned. |
| GetTransaction | [GetTransactionRequest](#pb.GetTransactionRequest) | [GetTransactionResponse](#pb.GetTransactionResponse) | Get a transaction given its hash.

**Requires TxIndex** |
| GetRawTransaction | [GetRawTransactionRequest](#pb.GetRawTransactionRequest) | [GetRawTransactionResponse](#pb.GetRawTransactionResponse) | Get a serialized transaction given its hash.

**Requires TxIndex** |
| GetAddressTransactions | [GetAddressTransactionsRequest](#pb.GetAddressTransactionsRequest) | [GetAddressTransactionsResponse](#pb.GetAddressTransactionsResponse) | Returns the transactions for the given address. Offers offset, limit, and from block options.

**Requires AddressIndex** |
| GetRawAddressTransactions | [GetRawAddressTransactionsRequest](#pb.GetRawAddressTransactionsRequest) | [GetRawAddressTransactionsResponse](#pb.GetRawAddressTransactionsResponse) | Returns the raw transactions for the given address. Offers offset, limit, and from block options.

**Requires AddressIndex** |
| GetAddressUnspentOutputs | [GetAddressUnspentOutputsRequest](#pb.GetAddressUnspentOutputsRequest) | [GetAddressUnspentOutputsResponse](#pb.GetAddressUnspentOutputsResponse) | Returns all the unspent transaction outputs for the given address.

**Requires AddressIndex** |
| GetUnspentOutput | [GetUnspentOutputRequest](#pb.GetUnspentOutputRequest) | [GetUnspentOutputResponse](#pb.GetUnspentOutputResponse) | Looks up the unspent output in the utxo set and returns the utxo metadata or not found. |
| GetMerkleProof | [GetMerkleProofRequest](#pb.GetMerkleProofRequest) | [GetMerkleProofResponse](#pb.GetMerkleProofResponse) | Returns a merkle (SPV) proof that the given transaction is in the provided block.

**Requires TxIndex*** |
| SubmitTransaction | [SubmitTransactionRequest](#pb.SubmitTransactionRequest) | [SubmitTransactionResponse](#pb.SubmitTransactionResponse) | Submit a transaction to all connected peers. |
| SubscribeTransactions | [SubscribeTransactionsRequest](#pb.SubscribeTransactionsRequest) | [TransactionNotification](#pb.TransactionNotification) stream | Subscribe to relevant transactions based on the subscription requests.

This RPC does not use bi-directional streams and therefore can be used with grpc-web. You will need to close and re-open the stream whenever you want to update the addresses. If you are not using grpc-web then SubscribeTransactionStream is more appropriate.

**Requires TxIndex to receive input metadata** |
| SubscribeTransactionStream | [SubscribeTransactionsRequest](#pb.SubscribeTransactionsRequest) stream | [TransactionNotification](#pb.TransactionNotification) stream | Subscribe to relevant transactions based on the subscription requests. The parameters to filter transactions on can be updated by sending new SubscribeTransactionsRequest objects on the stream.

Because this RPC is using bi-directional streaming it cannot be used with grpc-web.

**Requires TxIndex to receive input metadata** |
| SubscribeBlocks | [SubscribeBlocksRequest](#pb.SubscribeBlocksRequest) | [BlockNotification](#pb.BlockNotification) stream | Subscribe to notifications of new blocks being connected to the blockchain or blocks being disconnected. |

 



## Scalar Value Types

| .proto Type | Notes | C++ | Java | Python | Go | C# | PHP | Ruby |
| ----------- | ----- | --- | ---- | ------ | -- | -- | --- | ---- |
| <a name="double" /> double |  | double | double | float | float64 | double | float | Float |
| <a name="float" /> float |  | float | float | float | float32 | float | float | Float |
| <a name="int32" /> int32 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="int64" /> int64 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="uint32" /> uint32 | Uses variable-length encoding. | uint32 | int | int/long | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="uint64" /> uint64 | Uses variable-length encoding. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum or Fixnum (as required) |
| <a name="sint32" /> sint32 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sint64" /> sint64 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="fixed32" /> fixed32 | Always four bytes. More efficient than uint32 if values are often greater than 2^28. | uint32 | int | int | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="fixed64" /> fixed64 | Always eight bytes. More efficient than uint64 if values are often greater than 2^56. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum |
| <a name="sfixed32" /> sfixed32 | Always four bytes. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sfixed64" /> sfixed64 | Always eight bytes. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="bool" /> bool |  | bool | boolean | boolean | bool | bool | boolean | TrueClass/FalseClass |
| <a name="string" /> string | A string must always contain UTF-8 encoded or 7-bit ASCII text. | string | String | str/unicode | string | string | string | String (UTF-8) |
| <a name="bytes" /> bytes | May contain any arbitrary sequence of bytes. | string | ByteString | str | []byte | ByteString | string | String (ASCII-8BIT) |

