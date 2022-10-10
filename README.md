# Decentralized-Smart-Contract-Lottery
  **Fully decentralized Smart Contract Lottery that enables users to experience fair play, proven on chain.**
  
  ## The Lottery
  Users are able to buy tickets for a limited time.
  
  Funds from purchases are stored in the contract.(Only the contract itself can use these funds)
  
  After purchase time ends a random winner is selected. Completed via random number generation.
  
  A function for a surprise winner exists, which will award a randomly generated winner with 50% of the gathered funds, at a random time.
  At the end of the Lottery another winner will collect all gathered funds left.
  
  The Ticket Factory can deploy new Lotteries(Proxies). The Beacon points to the address of the original implementation. 
  
  ## Implementation
Implementing the following:

1.**Chainlink VRF** - for Random Winner picking.

2.**Beacon Proxy Pattern** - for creating and maintaining new lottery rounds.

3.Lotteries can be deployed via **Create 2**.

4.Tickets are represented by **NFTs**(**ERC721**) and their additional data can be **stored off-chain**

4.Lottery Tickets can be **purchased with URI**
  
  ## The Contracts
  #### Lottery Manager 
 
  Contract is created for the purpose of simpler management.
  
  #### Ticket (Lottery)

 An ERC721URIStorageUpgradeable contract
 
 Supports minting tickets from a certain block onwards for a certain period of time
 
 A user has to fund the Chainlink VRF Consumer with LINK tokens and then be rewarded with 3 free tickets
 
 At the end a winner is chosen using Chainlink VRF

#### TicketProxy

Simple beacon proxy using the Ticket contract as its implementation

#### TicketBeacon

Simple beacon managing the implementation used by the TicketProxy

#### TicketFactory

Ownable factory contract for deploying ticket proxies

Supports determministic deployment using the create2 opcode

Restricted access for deployment to only owner

#### WinnerPicker

VRF Consumer using chainlink vrf setup for mainnet or rinkeby

Creates requests for generating new number

Saves msg.sender and its callback function signature used later to pass the received random number from chainlink


## Setup


```git clone https://github.com/asparuhdamyanov/Decentralized-Smart-Contract-Lottery.git```

```cd NFT-lottery```

``` yarn```

```npm run test or npx hardhat test```




