# defi **(sync)**

### raffle 奖池

- (仓库) https://github.com/Raffleth

- (合约) https://github.com/Raffleth/protocol

- (前端) https://github.com/Raffleth/subgraph

- (官网) https://raffl.xyz/

### loan 借贷

- (仓库) https://github.com/compound-finance

- (合约) https://github.com/compound-finance/compound-protocol

- (前端) https://github.com/compound-finance/compound-js

- (官网) https://compound.finance/

### dex 交易所

## uniswap

- (仓库) https://github.com/Uniswap

- (合约) https://github.com/Uniswap/v2-core

- (前端) https://github.com/compound-finance/compound-js

- (官网) https://app.uniswap.org/

## raydium

- (仓库) https://github.com/raydium-io

- (官网) https://raydium.io/

## 数据库设计

### 表结构说明

1. **pairs（交易对表）**
   - 存储所有交易对的基本信息
   - 包含代币地址、符号、精度、储备量等信息
   - 使用address作为唯一索引

2. **tokens（代币表）**
   - 存储所有代币的基本信息
   - 包含代币地址、符号、名称、精度、总供应量等信息
   - 使用address作为唯一索引

3. **swaps（交易记录表）**
   - 记录所有交易历史
   - 包含交易对、交易金额、价格等信息
   - 关联pairs表

4. **liquidity（流动性表）**
   - 记录流动性提供者信息
   - 包含代币数量、LP代币数量等信息
   - 关联pairs表

5. **sync_blocks（同步区块表）**
   - 记录同步进度
   - 支持多链同步
   - 便于断点续传

### 索引设计
- pairs表：token0_address, token1_address
- tokens表：symbol
- swaps表：pair_id + timestamp, block_number
- liquidity表：pair_id + provider, block_number

### 数据类型说明
- 地址类型：VARCHAR(42)
- 金额类型：NUMERIC(36,18)
- 时间类型：TIMESTAMP
- 区块号：BIGINT
