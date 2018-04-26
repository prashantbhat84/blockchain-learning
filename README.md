# Setup a Consortium/Private network with PoA
# Clique documentation
# Part of the course on Ethereum
http://www.acloudfan.com
http://www.bcmentors.com

https://github.com/ethereum/EIPs/issues/225


1. Create directories node1   node2
    * Chaindata will go under the subdirectory 'data'
2. Create accounts:
    * geth --datadir ./node1/data  account new
    bc758cc69671f3bb2a4f0ab9aa3ca233d0074c0a

    * geth --datadir ./node2/data  account new
    5813e7391b56a2e08ce5f6ac069d9eeb45ff84d8

3. Run the puppeth tool to generate the genesis.json file

4. Initialize node1 & node2

   cd node1
   geth --datadir ./data init ../test1.json

   cd node2
   geth --datadir ./data init ../test1.json

5. Setup bootnode 
   * we will use the bootnode setup under ../privnw_one/bnode
   * Launch Bootnode
   * Get <<enode>> information for the bootnode

6. Set up the launch script for ./node1 and ./node2 with <<enode>> of bootnode
   * Hint use the script .../privnw_one/node1/launch.boot.sh

7. Launch commands for Starting the node1, node2

* Node 1 Launch command - Mining is ON
======================================
geth --networkid 1015 --datadir "./data" --bootnodes 'enode://e4e56e8205464af090be4923b9764ccb54f6c28ef71bff7c4cd7b8feabf98e9cfc3a061d76bfd88bd898c0c43296c9653c7f58b5f664823b2d43579c45143587@127.0.0.1:30310' --port  30303 --ipcdisable --syncmode full --rpc --rpccorsdomain "*" --rpcport 8545 --unlock 0x5dfde8d473baadb107e6ba5d5b1584e90231a27e --password password.txt  --mine console

* Node 2 Launch command
=======================
geth --networkid 1015 --datadir "./data" --bootnodes '  --port  30304 --ipcdisable --syncmode full --rpc --rpccorsdomain "*" --rpcport 8546 --unlock 0x087bb349e7383bfa61c169b1af5d3375599403aa --password password.txt   console

*Node 3 launch command

========================
geth --networkid 1015 --datadir "./data" --bootnodes 'enode://e4e56e8205464af090be4923b9764ccb54f6c28ef71bff7c4cd7b8feabf98e9cfc3a061d76bfd88bd898c0c43296c9653c7f58b5f664823b2d43579c45143587@127.0.0.1:30310'  --port  30304 --ipcdisable --syncmode full --rpc --rpccorsdomain "*" --rpcport 8547--unlock 0x796edae95f4f28c4c812222f9e01632629db631c --password password.txt   console

    * Node1 - Replace <<enode>>
    geth --networkid 1015 --datadir "./data" --bootnodes '<<enode>>'  --port  30303 --ipcdisable --syncmode full --rpc --rpccorsdomain "*" --rpcport 8545 --unlock --password password.txt console 

    * Node2 - Replace <<enode>>
    geth --networkid 1015 --datadir "./data" --bootnodes '<<enode>>'  --port  30304 --ipcdisable --syncmode full --rpc --rpccorsdomain "*" --rpcport 8546 --unlock --password "password.txt" console 

8. Deploy a contract on node1 and execute the contract on node2
   * Use any tool for execution
   * How about enabling RPC on both node1/node2 and using Remix 
     RPC ports need to be different for nod1 & node2
   