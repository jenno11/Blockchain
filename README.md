## blockchain-homework

# Part 1
I created two nodes (zbank1 & zbank2) for my testnet blockchain with the following commands:

./geth --datadir zbank1 account new
./geth --datadir zbank2 account new

<img width="879" alt="image1" src="https://user-images.githubusercontent.com/84065878/140633168-a8d2e5d5-8f25-45ec-8dc3-a640d5856322.png">

This command will prompt you to create a password for each node. After setting a password for each node, a public key and secret key file location is generated for the node. For future reference, store each node's password, public key, and secret key file location in a separate file.

# Store node credentials for future use:

<img width="581" alt="Screen Shot 2021-11-07 at 4 13 25 pm" src="https://user-images.githubusercontent.com/84065878/140633210-cce061d7-edc9-44d7-8382-8e188455b639.png">

# Part 2
1. Run ./puppeth in your terminal. This initiates the process of creating your network and configuring your genesis block.

2. Next, enter a network name of your choice when prompted. For my testnet, I used a network name of "homework".

3. At the next prompt, select option 2, "Configure new genesis".

4. Select "Clique - proof-of-authority" (option 2) as your consensus engine.

5. At the next prompt, hit enter to accept the default option for blocktime.

6. At the next prompt, enter the public key of the nodes created during Part 1 above to seal the node addresses. The node's public key addresses should have been stored for later use. Make sure to omit the first two characters ("0x") of the public key when entering the address into your terminal.

7. Pre-fund both node accounts by repeating the above step at the next prompt.

8. Select "no" when asked to pre-compile node addresses with 1 wei.

9. The next step defines the chain/network ID. Enter a three-digit code. For example, I used a chain ID of "232" for my testnet. Store the chain ID in a separate file for future reference.

10. Setting the chain ID will conclude the process of configuring your genesis block, and send you back to the first prompt. Once there, select "Manage existing genesis" (option 2).

11. Select "Export genesis configurations" (option 2). This will create 2 files and fail to create 2 files. For the purposes of running our blockchain, we'll only need one of the two files created (networkname.json).

<img width="802" alt="image2" src="https://user-images.githubusercontent.com/84065878/140633281-9c4610b3-1af2-4f4c-ac36-1c5120237370.png">

# Part 3

I initialized my nodes with the following commands:

./geth --datadir zbank1 init homework.json
./geth --datadir zbank2 init homework.json

<img width="1440" alt="initializenodes" src="https://user-images.githubusercontent.com/84065878/140633302-6fbe304f-1192-4105-8430-3881eb45d61c.png">

# Part 4

Run your first node with the following command:

./geth --datadir zbank1 --mine --minerthreads 1

<img width="1440" alt="image4" src="https://user-images.githubusercontent.com/84065878/140633367-6dc5284e-3c0f-4022-86ed-b54418fb69c6.png">

Prior to running our second node, we'll need to save one more piece of information: the first node's enode address. We should see the enode address in our terminal window after running the above geth command to run the first node. The enode address will be to right of a message that says "Started P2P networking". We'll need this enode address to sync our second node with the first node. Find the address and store it in a separate file.

<img width="580" alt="Screen Shot 2021-11-07 at 4 20 39 pm" src="https://user-images.githubusercontent.com/84065878/140633414-86673c93-f7c0-4eac-83c8-e1784072c8ac.png">

In a new terminal window, run your second node with the followng command:

./geth --datadir node2 --port 30304 --rpc --bootnodes "enode://b55e09585ae0afe0d9514bea3bdf5d64997a0b738e8475403ab360b54defa36b553fc325ce42dff879b6bcd42ace1297270994269ef7b2fc6df0f522df1ec330@127.0.0.1:30303"

# Part 5

- Open MyCrypto application

- Set up a custom network by selecting "Change Network" in the bottom left corner of the MyCrypto window, and then selecting "Add Custom Node".

- Set the parameters of your custom network as follows:

- Node Name: Set equal to the network name you defined in puppeth
- Network: Custom
- Network Name: Set equal to the network name you defined in puppeth
- Currency: Set to "ETH"
- Chain ID: Set equal to the chain ID you defined when configuring your genesis block
- URL: Set to http://127.0.0.1:8545

<img width="866" alt="Screen Shot 2021-11-07 at 4 08 37 pm" src="https://user-images.githubusercontent.com/84065878/140633929-aa275d80-912e-4fdd-99ac-159ca6c2f4e9.png">


- After connecting to your custom network, navigate to the "View & Send" tab to initialize your transaction

- Select "Keystore File" and select your first node's keystore file. The location of this file should have been saved in a previous step. Use the node password to unlock the keystore file. After unlocking, you'll arrive at a transaction page. You should see your first node's pre-funded balance on the upper right of this page:

<img width="1216" alt="Screen Shot 2021-11-07 at 4 00 45 pm" src="https://user-images.githubusercontent.com/84065878/140633951-c30931cd-8181-4716-ae7e-b41a0f266019.png">

Initiate a transfer from your first node to the second node:
Enter second node address in "To Address" field.
Enter an amount of ETH in the "Amount" field.
Select "Send Transaction".
Sending the transaction will prompt a dialog box at the bottom of the window that reads "Check TX Status". Click on "Check TX Status" to see the status and full details of the transaction.



