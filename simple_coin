pragma solidity >=0.7.0 <0.9.0;

contract Coin{
    address public minter;
    mapping(address => uint) public balances;
    
    event Sent(address from, address to, uint amount);
    
    constructor(){
        minter = msg.sender; //msg allows us to access special variables thats available for us in the blockchain
    }
    
    function mint(address receiver, uint amount) public{
        require(msg.sender == minter);
        require(amount < 1e60);
        balances[receiver] += amount;
    }
    
    function send(address receiver, uint amount)public{
        require(amount<= balances[msg.sender], "Insufficient balances.");
        balances[msg.sender] -= amount;
        balances[receiver] += amount;
        emit Sent(msg.sender, receiver, amount); //emit triggers the event and in this case the event locks the transaction into the blockchain
    }
}
