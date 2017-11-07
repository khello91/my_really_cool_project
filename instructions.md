# Smart Contract Manual

These are instructions on how to use ERC20 token contract and ICO contract deployed on ethereum blockchain, the instructions use CubaazCoin contracts as an example.

## General Instructions
0. **TO START ICO**  

	Go to [TOKEN CONTRACT PAGE](https://etherscan.io/address/0x452B8B085CED1968b6faDE6C2Dcf608c5c297F31#code) on etherscan, and [ICO CONTRACT PAGE](https://etherscan.io/address/0x88aa2aa27cabfbf2245448d368fd336641477f0e#code) on etherscan, from there you can copy the **Contract Address** and **ABI** for the contracts

	Go to https://wallet.ethereum.org After installing and logging into *[Metamask](http://metamask.io)* and importing the owner account (`0x4a81247ce8e94d6f1f0d6065bc62d3eb76904afd`) in metamask using then owner private key.

	In https://wallet.ethereum.org go to `contracts -> watch token`, paste the contract address for token.

	Send the tokens which you want to sell, to [ICO contract address](https://etherscan.io/address/0x88aa2aa27cabfbf2245448d368fd336641477f0e#code) (`0x88aa2aa27cabfbf2245448d368fd336641477f0e`), from https://wallet.ethereum.org -> `Send` -> Click on CubaazCoin (Or your token) and send the amount you wanna send.

	In https://wallet.ethereum.org, go to `contracts -> watch contract` paste the **contract address** and **ABI** for ICO contract, give it any name, after it is added to wallet click on it, from `pick a function` click `start sale` put a delay of 0 and execute. It's Started!



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
	2.1 eg. for [CubaazCoin ICO](https://etherscan.io/address/0x88aa2aa27cabfbf2245448d368fd336641477f0e#code), use this: https://api.etherscan.io/api?module=account&action=tokenbalance&contractaddress=0x452B8B085CED1968b6faDE6C2Dcf608c5c297F31&address=0x88aa2aa27cabfbf2245448d368fd336641477f0e&tag=latest and divide it by 10<sup>8</sup>
	``` javascript
	$.get("https://api.etherscan.io/api?module=account&action=tokenbalance&contractaddress=0x452B8B085CED1968b6faDE6C2Dcf608c5c297F31&address=0x88aa2aa27cabfbf2245448d368fd336641477f0e&tag=latest")
	.then(function(data){
		console.log(BALANCE = data.result/Math.pow(10,8))
	})
	// And then subtract it from inital ICO balance
	// TOKENS_SOLD = INITIAL_ICO_BALANCE - BALANCE
	```



