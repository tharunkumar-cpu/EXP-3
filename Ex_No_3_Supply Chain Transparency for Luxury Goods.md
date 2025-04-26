# Aim:
To develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
# Namw:THARUN K
# Reg no:212222040172
# Date:26/04/2026
# Algorithm:
The manufacturer records product creation details on-chain.


The product moves through different supply chain checkpoints.


The ownership of the product can be transferred securely.


Buyers can verify the product’s authenticity.


# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LuxurySupplyChain {
    struct Product {
        string name;
        address currentOwner;
        bool verified;
    }

    mapping(uint256 => Product) public products;

    event ProductRegistered(uint256 productId, string name);
    event OwnershipTransferred(uint256 productId, address newOwner);

    function registerProduct(uint256 productId, string memory name) public {
        require(products[productId].currentOwner == address(0), "Product already registered");
        products[productId] = Product(name, msg.sender, true);
        emit ProductRegistered(productId, name);
    }

    function transferOwnership(uint256 productId, address newOwner) public {
        require(products[productId].currentOwner == msg.sender, "Not the owner");
        products[productId].currentOwner = newOwner;
        emit OwnershipTransferred(productId, newOwner);
    }

    function verifyProduct(uint256 productId) public view returns (string memory, address, bool) {
        Product memory p = products[productId];
        return (p.name, p.currentOwner, p.verified);
    }
}
```
# Expected Output:
A luxury good (e.g., a Rolex watch) is registered on-chain.


Ownership is transferred at every checkpoint.


Buyers can check the authenticity before purchasing.


# High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.
# out put:
register:
![Screenshot (50)](https://github.com/user-attachments/assets/5f205c9c-1a38-4825-9a03-69e11fccb2bf)

Transaction:
![Screenshot (51)](https://github.com/user-attachments/assets/bd75ee50-b4ad-459f-867a-b1a8e7361427)

Verification:
![Screenshot (52)](https://github.com/user-attachments/assets/25cd549c-0b4f-4efd-bce1-e646d1435676)


# RESULT : 
A smart contract that tracks the supply chain of luxury goods and ensuring authenticity is successfully executed.
