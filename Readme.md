<h1>Cryptozombies Bonus Task - Blockship </h1>

<li>Version of solidity used: pragma solidity 0.5.16<br>
<li>All smart contracts compiled into a truffle project<br>
<li>Unit Testing done as required (All functions passed)<br>
<li>Deployed to local blockchain Ganache<br>

  
<h3>Cryptozombies Smart Contract </h3>
<li>This smart contract was made to serve as a collective compilation of all the contracts.<br>
<li>It has no functions to it, instead only has an import statement.<br>
<li>This was for ease of use during unit testing.<br>

<h3>ERC721 Smart Contract </h3>
<li>This contract holds the ERC721 standard for simplified implementations into other contracts.<br>
 
<h3>Ownable Smart Contract </h3>
<li>The Ownable contract has an owner address, and provides basic authorization control functions,
this simplifies the implementation of "user permissions".<br>
<li>'onlyowner' function from this contract is used in other contracts to restrict the caller of the function to the owner.<br>

<h3>Safemath Smart Contract </h3>
<li>This smart contract contains mathematical functions for use in the other smart contracts.<br>
<li>Throws error when overflow occurs<br>
  
<h3>Zombieattack Smart Contract </h3>
<li>Imports from zombiehelper smart contract. <br>
<li>attack function is callable by the owner. <br>
<li>It creates two zombies and assigns them the ids repectively. <br>
<li>Calls the randMod funtion to create a hash which acts as the victory probability. <br>
<li>Hash is compared with the preset value of 70 resulting in two different results through an if-else statement. <br>
<li>if statement results in owner's zombie taking the win. A level and wincount is increased by one, whereas enemy loss count is inremented by one. feedandMultiply function is then triggered. <br>
<li>else statment results in tragetzombie's win. Owner's zombie's losscount is incremented by 1 and wincount of target zombie increases by 1. triggercooldown funtion is then called. <br>

<h3>Zombiefactory Smart Contract </h3>
<li>Imports from the ownable and safemath smart contracts. <br>
<li>NewZombie event is declared. <br>
<li>dnadigits and dnamodulus are declared to ensure that zombiedna is 16 digits. <br>
<li>cooldown time is also declared. <br>
<li>Zombie struct is declared which is then declared as an array. <br>
<li>two mappings: zombietoowner and ownerzombiecount are declared to store zombies and their number to a specific address. <br>
<li>createzombie function is called internally to create a zombie for a specific address. It is stored in the mappings and the ownercount mapping is also updated. <br>
<li>Event of newzombie is also emitted to signify the creation of a new zombie. <br>
<li>GeneraterandomDna function creates a hash through the string entered. The hash is converted to 16 digits through dnamodulus and works as the dna of the new zombie. <br>
<li>Createrandomzombie functions checks if the address has 0 zombies before implementing the two above funtions to create a new zombie. <br>
   
<h3>Zombiefeeding Smart Contract </h3>
<li>Imports from zombiefactory smart contract. <br>
<li>KittcyInterface is declared for ease of use (Zombies eat kitties) <br>
<li>onlyOwnerof modifier is declared. <br>
<li>setKitty Contract address is called to set the address in the kitty interface. <br>
<li>triggercooldown function is declared internally. It sets the zombie on cooldown after attacking. <br>
<li>is ready function is declared to signify the end of cooldown time.<br>
<li>feedandmultiply function is declared to create a new kitty zombie. A new hash is made for the dna of the kitty zombie. A new zombie is created and triggercooldown is called at the end of the funtion. <br>
<li>feedonkitty function is used to implement the kittydna in the feedandmultiply function. <br>
  
<h3>Zombiehelper Smart Contract </h3>
<li>Imports from zombiefeeding smart contract.<br>
<li>Levelup fee is declared. <br>
<li>Levelup reward functions are declared. <br>
<li>abovelevel mobidifer checks if zombie is above certain level. <br>
<li>withdraw funtion is callable by owner. It allows balance to be transfered. <br>
<li>setLevelupfee function is used to modify the levelupfee. (Callable only by owner) <br>
<li>ChangeName function allows zombie name to be changed (a reward for leveling the zombie to level 2). <br>
<li>ChangeDna funtion allows zombie dna to be changed (a reward for leveling the zombie to level 20). <br>
<li>getZombiesbyowner function returns the number of zombies saved on an address. <br>

<h3>Zombieownership Smart Contract </h3>
<li>imports from zombieattack, erc721 and safemath smart contracts. <br>
<li>implementation of ERC721 token takes place in this contract<br>
<li>mapping of zombieApprovals is declared. <br>
<li>balanceof function updates the ownerZombieCount mapping. <br>
<li>ownerof function updates the zombietoowner mapping. <br>
<li>transfer function transfers a zombie from one address to another. It updates the mappings and emits the transfer event to signify the completion of the process. <br>
<li>transferfrom funtion checks the zombieapporval mapping before allowing the transfer funtion run. <br>
<li>approve function is used to update the zombieapproval mapping. <br>
  
<h3>UnitTesting </h3>
Once the contract is deployed to the mainnet blockchain, it cannot be changed. The following unit tests are conducted to ensure the workability of the smart contracts. <br>
<li>The first test: Checks if a new zombie is created and stored at the address. <br>
<li>The second test: Ensures that only one zombie is created per address. <br>
<li>The third test: Allows a zombie to be transferred to the different address using a one step scenario. <br>
<li>The fourth and fifth test: Allows zombie to be transferred to a new address using a two-step scenario. This allows an approval function for a set transaction; any apporved address can then call the transfer function. <br>
<li>The sixth test: Ensures that zombies can attack other zombies. Also checks if the cooldown function is working properly. <br>
  
