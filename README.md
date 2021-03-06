# EOS setup and sample app
##  **SETUP**
 **Prerequisite**
- Git
- Ubuntu 16 or 18 LTS  (Ubuntu 16.10 recommended)

**System Requirements (all platforms)**
- 7GB RAM free required
- 20GB Disk free required

**Overview**
EOS comes with mainly three modules.
- nodeos  - the core EOSIO node daemon
- cleos - command line interface to interact with the blockchain and to manage wallets 
- keosd - component that securely stores EOSIO keys in wallets. 

![N|Solid](https://files.readme.io/8f31cfd-Basic-EOSIO-System-Architecture.png)

 **Initial installation**
```sh
$ git clone https://github.com/eosio/eos --recursive
$ cd eos
```
It will download all the EOS code and its sub-modules

**Build the code**
EOS code can built with multiple ways based on the platform and the desired use.
- Autobuild Script
- Docker compose
- Manual build
- Install executables

Autobuild script is the one suitable for the developers and we are setting up that model.
```sh
$ ./eosio_build.sh 
```
`This will take a  couple of hours depending on the spec of machine`

**Build validation**
Test the build operation’s status(Validation Test) in eos/build directory using the following testing commands.
```sh
#Start mongo
$ ~/opt/mongodb/bin/mongod -f ~/opt/mongodb/mongod.conf &
$ cd build
$ make test
```
**Install the executables**
```sh
$ sudo make install
```
#### **Single node network**
After building the project, you can start the single node by running nodeos
```sh
$ cd ~/eos/build/programs/nodeos
$ ./nodeos -e -p eosio --plugin eosio::wallet_api_plugin --plugin eosio::chain_api_plugin --plugin eosio::history_api_plugin 
```
-e :-    Enable block production
-p  :-   ID of producer controller by the node
--plugin :- To enable multiple plugins

Nodeos uses a configuration folder.The config file ~/.local/share/eosio/nodeos/config can be found in this location.If config.ini is not found a default config.ini is created.

*Issues may arise:-*  
*3190000 block_log_exception: Block log exception*
*Block log was not setup properly with genesis information.*
*Solution* 
*Clear this folder for the issue :-*
*rm -rf ~/.local/share/eosio/nodeos/data*
*Or  ./nodeos --replay-blockchain --hard-replay-blockchain*

#### **Wallet Creation**
Open a new terminal
```sh
$ cd ~/eos/build/programs/cleos 
$ ./cleos wallet create  -n ``<your wallet name> ``
$ ./cleos create key
```
Sample Response
``Private key: 5JmJyTf9cYemDctq3a28UM2YDmr3eDStsHSXv1VqgUbCaHTuCbn``
   ``Public key: EOS8akHPngGi1nfvR55WqiGrTeCtsSLZRvAGT5LBRdrXDmoqQpSXw``

**Import  Private key**
```sh
./cleos wallet import ``<privatekey>``
```
#### **Sample App**
###### ***Coming Soon***

References: [EOSIO](https://developers.eos.io/eosio-nodeos/docs)

Contributors:
- [Crissi](https://github.com/crissiaccubits)
- [Goutham](https://github.com/goutham-ab)
