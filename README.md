# Aries Cloud Agent - Python (ACA-Py) -Controller

This project consists of a implementation of an Aca-Py Controller and a user interface to interact with the controller, allowing the user to create, see and accept connections. 

ACA-py (aries-cloudagent-python) is the python application that interacts with other Aries agents. The controller is the application that interacts with the admin APIs of ACA-py.

## Run ACA-Py

Before starting the controller it is necessary to:
1. Install the prerequisites for running Aca-Py;
2. Authenticate a Decentralized Digital Identity (DID)
3. Create a Wallet
4. Start Aca-Py

### Installing Prerequisites:
This are the prerequisites for running Aca-py:
1. Python3
2. pip
3. Python3_indy
4. Indy_cli
5. libsodium

To install the prerequisites on Linux:
```
sudo apt update
sudo apt install python3-pip
pip install aries-cloudagent
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE7709D068DB5E88
sudo add-apt-repository "deb https://repo.sovrin.org/sdk/deb bionic master"
sudo apt update
sudo apt install -y libindy
pip3 install python3_indy
sudo apt install -y indy-cli
sudo apt install libsodium-dev
```
### Authenticating a DID:
To Authenticate a New DID:
https://indy-test.bosch-digital.de/

### Create a Wallet:
Provide yout public IP address in `endpoint` and change `wallet-name` and `wallet-key` to match the authenticaded wallet.

```
aca-py provision \
--wallet-type indy \
--endpoint https://provide_your_own_public_ip_address_endpoint.com \
--seed PROVIDE_SEED_USED_ON_BOSH_WEBSITE \
--wallet-name PROVIDE_YOUR_WALLET_NAME \
--wallet-key PROVIDE_YOUR_WALLET_SECRET_KEY \
--genesis-url https://indy-test.bosch-digital.de/genesis

### Start Aca-Py:
Make appropriate changes to match the wallet provision.

aca-py start \
--inbound-transport http 0.0.0.0 8000 \
--endpoint https://provide_your_own_public_ip_address_endpoint.com \
--outbound-transport http \
--admin 0.0.0.0 8001 \
--webhook-url http://localhost:8002 \
--genesis-url https://indy-test.bosch-digital.de/genesis \
--wallet-type indy \
--wallet-name PROVIDE_YOUR_WALLET_NAME \
--wallet-key PROVIDE_YOUR_WALLET_SECRET_KEY \
--seed PROVIDE_SEED_USED_ON_BOSH_WEBSITE \
--admin-insecure-mode \
--label PROVIDE_YOUR_SSI_AGENT_LABEL \
--log-level debug \
--storage-type indy \
--auto-ping-connection \
--max-message-size 10485760 
```

# Run the ACA-Py Controller
## Controller
To run the ACA-Py Controller clone this repository and in the ACA-Py-Controller folder execute:
```
cd controller
npm install
npm start
```
## Front-end
To start front-end execute, go to Controller-Frontend folder and execute: 
```
cd frontend
npm install
npm start
```
Open the browser in http://localhost:3000