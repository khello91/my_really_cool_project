# Smart Contract Manual

These are instructions on how to use ERC20 token contract and ICO contract deployed on ethereum blockchain

## General Instructions

1. To show the amount of ETH raised, track the balance of the `wallet` address to which the ETH is going after being contributed using [Etherscan API](https://etherscan.io/apis#accounts), it will return the balance in wei, divide the balance by 10<sup>18</sup> to get the balance in ETH.  
	1.1 eg. for [CubaazCoin](https://etherscan.io/token/0x452B8B085CED1968b6faDE6C2Dcf608c5c297F31), track the balance of the `wallet` specified in [CubaazCoin ICO Contract](https://etherscan.io/address/0x88aa2aa27cabfbf2245448d368fd336641477f0e#code), using this: https://api.etherscan.io/api?module=account&action=balance&address=0x4a81247CE8E94d6f1F0d6065BC62d3eB76904aFD&tag=latest , divide the balance by 10<sup>18</sup> and show it.
	1.2 CODE:  
	``` javascript
	$.get("https://api.etherscan.io/api?module=account&action=balance&address=0x4a81247CE8E94d6f1F0d6065BC62d3eB76904aFD&tag=latest")
	.then(function(data){
		console.log(data.result/Math.pow(10,18))
	})
	```

2. To show the Tokens Sold, track the Token balance of ICO smart contract using [Etherscan API](https://etherscan.io/apis#tokens), and then divide the balance by 10<sup>decimals</sup>, eg. if your token has 8 decimals, divide it by 10<sup>8</sup>, and then subtract it from the initial token balance of ICO smart contract.

## ERC20 Token

