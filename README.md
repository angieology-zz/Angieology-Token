# Creating a Token on Ethereum

Remix + MetaMask 
Remix IDE and deploy on MetaMask test network

## Step 1
install Metamask Chrome extension: https://chrome.google.com/webstore/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn?hl=en
and sign in by creating a password, and save the 'seed' file. This automatically connects your browser to the ethereum blockchain network and also sets up an account for you. Don't worry it has no private info, so only you can access your account.

## Step 2
You will need to fund you account in order to deploy a contract on the network. This is called a Gas price. It's a metaphor for running an engine. In the top bar, find the dropdown that lets you select between different types of networks. Select the Ropsten test network. Click 'buy' => 'ropsten test faucet'. In the redirected page, request some test ether.

## Step 3
The ERC223 is the latest standard for a token on the ethereum network. It is a interface that defines a few methods you need at minimum. A method to transfer your token between accounts, to check how much you own, etc. This is written in solidity which is VERY similar to C, C# or Java. A few differences you might notice is that a class is called 'contract'. Just skim this for now:
https://github.com/Dexaran/ERC223-token-standard

## Step 4
http://remix.ethereum.org/ is a online Solidity IDE. When you deploy code from here, Metamask will automatically detect and fund from your account.
Create a new file with + in the top left corner. Name the file after your own token name, ie. 'MyToken.sol'

## Step 5
in the ERC223 repo, navigate to token.sol file. Copy this file into your new (blank) MyToken.sol file. You will notice it is importing 3 files from the repo, copy those files as well, all into one file in the remix IDE.

## Step 6
In the ERC223Token contract, which is the only 'contract' from the token.sol file, replace the contract name with your own token name. Add some init variables and a constructor that will set up how many tokens are in circulation, how many decimal points (denominations) of the token, etc. 
note: uint type is 256-bit by default, hence the casting
if the 'totalSupply' line confuses you, look up wei <=> eth charts. It is like, if you want $100 in ciruclation, but you have to state them in terms of pennies (2 decimal places).
Variables must be public to be read

```
/* standard properties of token */
    
    string public name;
    uint8 public decimals;
    string public symbol;
    uint public totalSupply;
    
    /*constructor will assign values to properties */
    
    function Angieology() {
        name = "Angela";
        decimals = 18; //ethereum has 18 decimals, bitcoin 8
        symbol = "AYL";
        totalSupply = 1000000 * 10 ** uint(decimals); 
        //I want a million tokens to exist in my contract
        //enables token to have 18 decimal places
        balances[msg.sender] = totalSupply;
    }
 ```
## Step 7
As long as there are no compile errors, select the run tab in remix IDE. Select the name of your contract in the drop down.
Click save icon to create a scenario.json file. Then click create.
 
## Step 8
It will lead you to a confirm box in metamask. Deploying the contract will take a few minutes, you can track the progress from your metamask. 
 
## Step 9
When complete, click the 'contract complete' in your account history. This will give you more info. Copy the contract address hash (not account address) into the 'Add Tokens' under 'tokens' tab. This will fund your account with your new token. Probably worth nothing but they are all yours.
 
## Step 10
if you want to trade your token or recieve tokens use myetherwallet.com
