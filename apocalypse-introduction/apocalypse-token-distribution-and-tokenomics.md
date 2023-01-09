# Apocalypse Token Distribution & Tokenomics

## <mark style="color:yellow;">Apocalypse Token Distribution</mark>

The token economics of the Apocalypse token are straightforward and designed to promote the long-term stability and security of the project. At launch, there will be no burning of tokens, with burning occurring gradually over time. To ensure the safety and security of the project, all tokens are locked and vest until 2025.&#x20;

This means that the liquidity pool will be locked for a period of two years, with no unlocked tokens. This ensures that the project has a strong foundation and is protected against potential market fluctuations or other risks. By gradually releasing tokens over time, the project can maintain a stable and sustainable token economy while also aligning with the long-term goals of the company.

![](<../.gitbook/assets/image (41).png>)

## <mark style="color:yellow;">Tokenomics</mark>

One of the key challenges faced by many non-fungible token (NFT) games is the inability to sustain a reward pool for players over an extended period of time. To address this issue, the Apocalypse game implements a tax on various in-game purchases, such as repairs, upgrades, crafting, and level ups, with the proceeds going towards the maintenance and growth of the reward pool.&#x20;

Specifically, 2% of the tax is allocated to a marketing wallet to fund ongoing advertising and marketing efforts, 1% is added to the liquidity pool to increase the floor price of the token, 1% is directed to a smart contract for buyback and burn activities to increase the value of the token and the amount of Binance Coin (BNB) in the liquidity pool, and 5% is added to the reward pool to sustain player rewards.

In addition to these taxes, there is also a transfer tax of 9% applied to both buy and sell transactions and transfers between wallets. The tax is hardcoded into the smart contract to never exceed 10%. These measures are designed to ensure the long-term sustainability and balance of the reward pool, providing players with a consistent and fair experience within the game.

Here's a simple breakdown to make it easier to understand:

* The Apocalypse game implements a tax on various in-game purchases to sustain the reward pool for players
* 2% of the tax is allocated to a marketing wallet to fund advertising and marketing efforts
* 1% is added to the liquidity pool to increase the floor price of the token
* 1% is directed to a smart contract for buyback and burn activities to increase the value of the token and the amount of Binance Coin (BNB) in the liquidity pool
* 5% is added to the reward pool to sustain player rewards
* A transfer tax of 9% is applied to both buy and sell transactions and transfers between wallets, with the tax hardcoded into the smart contract to never exceed 10%
* These measures are designed to ensure the long-term sustainability and balance of the reward pool and provide players with a fair and consistent experience within the game

{% hint style="success" %}
The Apocalypse (APOC) token is programmed to never have a tax rate higher than 10%. This restriction is hardcoded and cannot be changed. Below is the code snippet for reference.
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```solidity
/**
     * @dev Run internally to set all the fee settings and ensure that total fee is not more than 10%. 
     */
    function _setFees(
        uint256 _liquidityFee,
        uint256 _buybackFee,
        uint256 _rewardFee,
        uint256 _marketingFee,
        uint256 _feeDenominator
    ) internal {
        liquidityFee = _liquidityFee;
        buybackFee = _buybackFee;
        rewardFee = _rewardFee;
        marketingFee = _marketingFee;
        totalFee = _liquidityFee.add(_buybackFee).add(_rewardFee).add(_marketingFee);
        feeDenominator = _feeDenominator;
        require(totalFee < feeDenominator.div(100).mul(10), "Total fee should not be greater than 10%.");
    }
```
{% endcode %}
