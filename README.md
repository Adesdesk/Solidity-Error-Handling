# Project Title

Solidity-Error-Handling

## Description

A simple smart contract that implements one each of revert(), assert(), and require() statements.

## Getting Started

### Installing

* All necessary installations are pre-installed on Remix online IDE
* Copy the raw file "ErrorHandling.sol" of this repository
* Launch the Remix online IDE with the url https://remix.ethereum.org

### Executing program

* In Remix, create a new file inside the "contracts" folder on the File explorer displayed on the left
* Paste the raw copy from ErrorHandling.sol (as below) in the new file you created.
* Compile the contract by clicking on the "Solidity Compiler" button on the outermost left menu bar (or use the shortcut "Ctrl + S")
* Just below the "Solidity Compiler" button, find and use the "Deploy and Run transactions" button to deploy the smart contract
* On successful deployment, find and click on the "Deployed Contracts" heading to see a drop down of an interface through which the contract can be interacted with
* Find the provided test accounts under the "ACCOUNTS" field of the interface on the left
* Copy any of the addresses listed in the format 0x5B3...eddC4 (100 ether) for use as input to the interfaces that require an address when interacting with the contract
* Test interact with the various functions of the smart contract to see the error handling implementations in action.
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.7;

contract HandleErrors {

    // public variables here
    string public tokenName = "CrafterToken";
    string public tokenAbbreviation = "CRT";
    uint public totalSupply = 0;
    uint public minimumMintable = 100;

    // mapping variable here
    mapping(address => uint) public balances;

    // mint function
    function mint(address _address, uint _value) public {
        
        // implementing a require() statement
        require(_address == msg.sender, "Only the token owner can mint tokens");

        // implementing a revert statement
        if (_value < minimumMintable) {
            revert("Minimum amount of token mintable must be matched or exceeded");
        } else {
            totalSupply += _value;
            balances[_address] += _value;
        }         
    }

    // burn function
    function burn(address _address, uint _value) public {

        // implementing an assert() statement
        assert(balances[_address] >= _value);
        totalSupply -= _value;
        balances[_address] -= _value;
    }    
}
```

## Help

Ensure that the smart contract file is named with a ".sol" file extension

## Author(s)

Contributor's name and contact info

Name: Adeola David Adelakun

Email: adesdesk@outlook.com


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
