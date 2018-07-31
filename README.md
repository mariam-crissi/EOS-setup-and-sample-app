# EOS setup and sample app
##  **SETUP**
### **Prerequisite**
- Git
- Ubuntu 16.04.3 LTS  or above 64 bit
### **Initial installation**
>git clone https://github.com/eosio/eos --recursive


>cd eos

>./eosio_build.sh 

`This will take a  couple of hours depending on the spec of machine`

>cd build

>make test

>sudo make install

### **Single node network**
>cd ~/eos/build/programs/nodeos


>``./nodeos -e -p eosio --plugin eosio::wallet_api_plugin --plugin eosio::chain_api_plugin --plugin eosio::history_api_plugin ``

### **Wallet Creation**
Open a new terminal
>cd ~/eos/build/programs/cleos 

>./cleos wallet create  -n ``<your wallet name> ``

>./cleos create key

Sample Response

                               	 	 	
``Private key: 5JmJyTf9cYemDctq3a28UM2YDmr3eDStsHSXv1VqgUbCaHTuCbn``
   
   
   ``Public key: EOS8akHPngGi1nfvR55WqiGrTeCtsSLZRvAGT5LBRdrXDmoqQpSXw``

### **Import  Private key**
>./cleos wallet import ``<privatekey>``

## Sample App

# ***Coming Soon***