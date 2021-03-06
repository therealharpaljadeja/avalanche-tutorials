# How to mint your own ERC20 on Avalanche using Open Zeppelin

### This tutorial teaches you to deploy your own ERC20 token on Avalanche FUJI C-chain testnet.

### The steps to deploy on the mainnet are identical and the differences are mentioned in the tutorial.

## Contents
- [Adding the Avalanche FUJI C-chain to Metamask.](#adding-the-avalanche-fuji-c-chain-to-metamask)
- [Funding the Metamask using Faucet (FUJI C-chain Testnet only)](#funding-the-metamask-using-faucet-fuji-c-chain-testnet-only)
- [Writing code in Remix IDE](#writing-code-in-remix-ide)
- [Compiling and Deploying to Avalanche FUJI C-chain Testnet.](#-compiling-and-deploying-to-avalanche-fuji-c-chain-testnet)
- [Adding token to Metamask.](#adding-token-to-metamask)


### <u>Adding the Avalanche FUJI C-chain to Metamask</u>

1. [Click here to download Metamask](https://metamask.io/) (If not installed). 

2. Open up metamask and click the networks dropdown.

![network-select-dropdown](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/network-select-dropdown.png)

3. Click on Custom RPC to add other EVM based chains in our case Avalanche.

![select-custom-rpc](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/custom-rpc-click.png)

4. Let's add Testnet first then Mainnet.

5. Avalanche Testnet settings are as follows.
    - Network Name: Avalanche FUJI C-Chain
    - New RPC URL: https://api.avax-test.network/ext/bc/C/rpc
    - ChainID: 43113
    - Symbol: AVAX
    - Explorer: https://cchain.explorer.avax-test.network

6. Your metamask should look something like this.

![metamask-testnet-config](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/testnet-network-config.png)

7. If correct hit the "Save" button.

8. After save you should have a <u>"Avalanche FUJI C-chain"</u> option.

![after-testnet-save](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/after-testnet-save.png)

9. Configuration for Mainnet is as follows.
    - Network Name: Avalanche Mainnet C-Chain
    - New RPC URL: https://api.avax.network/ext/bc/C/rpc
    - ChainID: 43114
    - Symbol: AVAX
    - Explorer: https://cchain.explorer.avax.network/

10. The steps to add the network in case of mainnet are identical except the configuration.

### <u>Funding the Metamask using Faucet (FUJI C-chain Testnet only)</u>

1. Let's ask the faucet for some AVAX so that we can deploy contracts. [Faucet Link](https://faucet.avax-test.network/)

![faucet-page](https://github.com/therealharpaljadeja/avalanche-tutorials/blob/master/how-to-mint-erc20-using-openzeppelin/assets/faucet-page.png?raw=true)

2. Copy address from metamask.

![copy-address](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/copy-address.png)

3. Paste the address in the input, complete the captcha, and request AVAX.

![request-avax](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/request-avax.png)

4. You should get a transaction id which you can use to see the transaction on the [testnet block explorer](https://cchain.explorer.avax-test.network/).

![transaction-id-faucet](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/transaction-id-faucet.png)

5. Once the transaction completes you should see the funds in your metamask. ????

![funds-received-from-faucet](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/funds-received-faucet.png)

6. Hooray! ???? we now have funds that we can use to deploy smart contracts.


### <u>Writing code in Remix IDE</u>

1. Let's now write the code for the ERC20 token.

2. In this tutorial we will use the [Remix IDE](https://remix.ethereum.org/) for deploying smart contracts as it is beginner-friendly.

3. This is how the Remix IDE interface looks like and we can see our project files on the left.

![remix-ide-interface](https://github.com/therealharpaljadeja/avalanche-tutorials/blob/master/how-to-mint-erc20-using-openzeppelin/assets/remix-ide-interface.png?raw=true)

4. Let's create a file under the "contracts" folder for our token.

![create-file-remix](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/create-file-remix.png)

5. For this tutorial I named it "MyToken.sol" make sure to have the .sol extension. As a good practice, you can name the file with the same name as the token.

![file-created-remix](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/file-created-remix.png)

6. I have attached the code for the token in the same repository. You can use that code to deploy any basic ERC20 token, simply copy and paste it in the editor section. I have increased the font for tutorial purposes.

![code-editor-section](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/code-editor-section.png)

7. Let's one by one go through the code.

8. Line 1 is the license for the token very similar to the license in Github.

9. Line 2 is where we specify the solidity compiler version. (^ means anything above). So in our case, it is anything above 0.8.0. 

10. Solidity has been constantly pushing updates and there might be some breaking changes so you can keep an eye on the [docs](https://docs.soliditylang.org) for the same.

11. However once the contract is deployed it works forever!

12. Line 4 is where we take help from Openzeppelin and import the ERC20 token contract. Observe the url it starts with an "@" sign which means I am trying to import from npm. 

13. You should try to import contracts from npm however GitHub links are also supported. From my personal experience, I have faced problems while verifying contracts when I import from Github.

14. Line 6 is the name of the contract.

15. "Token is ERC20" - these words basically inherit the methods of ERC20 openzeppelin contract in our token contract. 

16. This also means we can override the openzeppelin methods and create a custom token with features like SafeMoon. ????

17. Line 7 is the constructor this is the first method that gets called immediately when the contract is deployed.

18. **You should specify the name and symbol of the your token here!**

![specify-name-and-symbol](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/specify-name-and-symbol.png)

19. Line 8 calls the _mint function which basically creates the tokens. You can see that it sends the tokens to the address that deployed this contract. *By default, the decimals is 18.*

![specify-token-supply](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/specify-token-supply.png)

20. **You should specify the token supply here and also if you want some custom address to receive the tokens on mint you can replace "msg.sender" with the address.**

21. That's the code to deploy the token using Openzeppelin.

###  <u> Compiling and Deploying to Avalanche FUJI C-chain Testnet</u>

1. Let's now compile the code to check if there are any errors.

2. To compile the shortcut is Ctrl / Command + S or you can click the icon shown in the image below.

![compile-icon](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/compile-icon.png)

3. Make sure you have the correct compiler selected from the dropdown. 

![select-compiler](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/select-compiler.png)

4. Once you are sure you can click the "Compile" button to compile the contract.

![compile-button](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/compile-button.png)

5. If the compile is successful you can see the green tick and options to publish the contract on IPFS as shown below.

![compile-successful](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/compile-successful.png)

6. It's time to deploy! Click the deploy icon as shown in the image below.

![deploy-icon](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/deploy-icon.png)

7. Make sure to select "Injected Web3" in the dropdown as shown in the image below.

![select-injected-web3](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/select-injected-web3.png)

8. Once selected you should see the network id and your address with your wallet balance.

![injected-web3-selected](https://github.com/therealharpaljadeja/avalanche-tutorials/blob/master/how-to-mint-erc20-using-openzeppelin/assets/injected-web3-selected.png?raw=true)

9. Select the correct contract from the dropdown as shown in the image below.

![select-correct-contract](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/select-correct-contract.png)

10. Once you select the correct contract ("MyToken.sol" in this case) you should see a single deploy button.

![correct-contract-selected](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/correct-contract-selected.png)

11. Click the "Deploy" button. 

12. You will get a "Confirm Transaction" prompt. You can click on the "Confirm" button.

![confirm-transaction-prompt](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/confirm-transaction-prompt.png)

13. Once confirmed you should get a metamask pop-up. Make sure you are on the correct network *(if you want to deploy on mainnet then you should be on mainnet)* and hit the "Confirm" button.

![metamask-popup](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/metamask-popup.png)

14. Once you confirm you should see the transaction in your metamask once that transaction confirms the token will be deployed! ????

![metamask-confirmed](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/metamask-confirmed.png)

15. Once the token gets deployed you should see it under the "Deployed Contracts" section.

![token-deployed](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/token-deployed.png)

16. The token is deployed! 

### <u>Adding token to Metamask.</u>

1. Let's now add the token to our metamask and see its balance.

2. Copy the address of the token by clicking the copy button as shown in the image below.

![copy-token-address](https://github.com/therealharpaljadeja/avalanche-tutorials/blob/master/how-to-mint-erc20-using-openzeppelin/assets/copy-token-address.png?raw=true)

3. In metamask switch to Assets and click on "Add Token". 

![assets-metamask](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/assets-metamask.png)

4. Once you paste the address metamask will automatically populate the symbol and decimals.

![adding-token](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/adding-token.png)

5. Click "Next" and you should see the token balance in case you didn't replace msg.sender.

![last-step-adding-tokens](https://raw.githubusercontent.com/therealharpaljadeja/avalanche-tutorials/master/how-to-mint-erc20-using-openzeppelin/assets/last-step-adding-tokens.png)

6. Once the tokens are added you should see it in the assets section. Done! ????