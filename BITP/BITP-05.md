# BITP-05: Swap Assets

`author: 22388o` `mandatory` `final`

In a DEX-style Uniswap scenario implemented using the RGB protocol, you can create a decentralized exchange platform that allows users to swap assets using the principles of automated market making (AMM).

1. Asset Tokenization: The RGB protocol enables the tokenization of various assets on the Bitcoin blockchain. In this scenario, you would tokenize different assets, such as cryptocurrencies or other digital assets, as RGB tokens. These RGB tokens would represent ownership or claim over the underlying assets.

2. Liquidity Pool Creation: Liquidity providers can contribute their RGB tokens to liquidity pools within the DEX. These liquidity pools are designed to facilitate asset swapping. Liquidity providers deposit their tokens into the pools, allowing other users to trade against those assets. The liquidity pools maintain a balanced supply of tokens to enable efficient trading.

3. Swap Mechanism: Users of the DEX can initiate swaps between different RGB tokens. When a user wants to swap one asset for another, they provide the input asset and specify the desired output asset. The swap mechanism calculates the appropriate trade based on the assets' current prices and the liquidity available in the pools.

4. Automated Market Making: The swap mechanism in the DEX operates based on an automated market making algorithm, similar to Uniswap. The algorithm determines the trade based on the ratio of assets in the liquidity pools, aiming to maintain a constant product of the pool's assets. This algorithm ensures that prices adjust dynamically based on supply and demand.

5. Trading Fees and Incentives: The DEX can implement trading fees to incentivize liquidity providers and contribute to the platform's sustainability. When users perform swaps, a portion of the traded assets can be collected as fees and distributed to liquidity providers as rewards. These rewards can be paid out in the form of RGB tokens or other incentives to encourage liquidity provision.

By combining the RGB protocol with the principles of automated market making, you can create a DEX-style Uniswap scenario where users can swap assets in a decentralized and automated manner. The RGB protocol provides the foundation for asset tokenization and transaction management, while the AMM algorithm ensures efficient and dynamic asset trading within liquidity pools.

## Implementation

Based on RGB-20 from [RGB-20: Fungible assets](https://standards.lnp-bp.org/rgb/lnpbp-0020)

```phyton
interface RGB20
    global spec :: RGBContract.DivisibleAssetSpec
    global data :: RGBContract.ContractData
    global created :: RGBContract.Timestamp
    global issuedSupply+ :: RGBContract.Amount
    global burnedSupply* :: RGBContract.Amount
    global replacedSupply* :: RGBContract.Amount
    public inflationAllowance* :: Zk64
    public updateRight?
    public burnEpoch?
    public burnRight*
    private assetOwner* :: Zk64

    genesis :: spec, data, created, issuedSupply, reserves {RGBContract.ProofOfReserves ^ 0..0xFFFF}
      -> assetOwner*, inflationAllowance*, updateRight?, burnEpoch?
        !! supplyMismatch | invalidProof | insufficientReserves

    op Transfer :: previous assetOwner+ -> beneficiary assetOwner+
      !! nonEqualAmounts

    op? Issue :: used inflationAllowance+, reserves {RGBContract.ProofOfReserves ^ 0..0xFFFF}
      -> issuedSupply, future inflationAllowance*, beneficiary assetOwner*
        !! supplyMismatch | invalidProof | issueExceedsAllowance | insufficientReserves

    op? OpenEpoch :: used burnEpoch -> next burnEpoch?, burnRight

    op? Burn :: used burnRight, burnedSupply, burnProofs {RGBContract.ProofOfReserves ^ 0..0xFFFF}
      -> future burnRight?
        !! supplyMismatch | invalidProof | insufficientCoverage

    op? Replace :: used burnRight, replacedSupply, burnProofs {RGBContract.ProofOfReserves ^ 0..0xFFFF}
      -> future burnRight?, beneficiary assetOwner+
        !! nonEqualAmounts | supplyMismatch | invalidProof | insufficientCoverage

    op? Rename :: used updateRight -> future updateRight?, new spec

     op? Swap :: source assetOwner+, destination assetOwner+, amount
      -> future source assetOwner+, future destination assetOwner+
        !! insufficientBalance | nonEqualAmounts
```


