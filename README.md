# Codemetacrafters
Solution 

// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {
    string public name;
    string public symbol;
    uint public totalSupply;

    mapping(address => uint) public balances;

    constructor(string memory _name, string memory _symbol, uint _totalSupply) {
        name = _name;
        symbol = _symbol;
        totalSupply = _totalSupply;
        balances[msg.sender] = _totalSupply;
    }

    function mint(address _recipient, uint _value) public {
        require(_value > 0, "Value must be greater than zero");
        
        totalSupply += _value;
        balances[_recipient] += _value;
    }

    function burn(address _owner, uint _value) public {
        require(_value > 0, "Value must be greater than zero");
        require(balances[_owner] >= _value, "Insufficient balance");
        
        totalSupply -= _value;
        balances[_owner] -= _value;
    }
}

