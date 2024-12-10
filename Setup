Important Commands for Setting Up Hyperledger Fabric 2.5.x LTS on Ubuntu 22.04

1. Verify and Install Prerequisites:

- `sudo apt update` (Updates package lists)
- `sudo apt-get install git` (Installs Git)
    - `git --version` (Verifies Git installation)
- `sudo apt-get install curl` (Installs cURL)
    - `curl --version` (Verifies cURL installation)
- Docker Installation:
    - `curl -fsSL https://get.docker.com -o get-docker.sh` (Downloads Docker installer script)
    - `sudo sh get-docker.sh` (Installs Docker)
    - `sudo usermod -aG docker $USER` (Adds user to docker group)
    - `sudo systemctl enable docker` (Optionally enables Docker daemon on startup)
    - `sudo systemctl start docker` (Starts Docker service)
    - `docker --version` (Verifies Docker installation)
- Docker Compose Installation:
    - `sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose` (Downloads Docker Compose)
    - `sudo chmod +x /usr/local/bin/docker-compose` (Sets executable permission)
    - `docker-compose --version` (Verifies Docker Compose installation)

2. Install and Set Up Go (if writing Go chaincode):

- `wget https://go.dev/dl/go1.20.2.linux-amd64.tar.gz` (Downloads Go installer)
- `sudo tar -xvf go1.20.2.linux-amd64.tar.gz` (Extracts Go)
- `sudo mv go /usr/local` (Moves Go directory)
- `mkdir -p $HOME/go/src/github.com/<your_github_userid>` (Creates Go project directory)
- Set Go Environment Variables:
    - Edit `~/.bashrc` (Open bash configuration file)
    - Add these lines (replace `<your_github_userid>`):

    ```
    export GOROOT=/usr/local/go
    export GOPATH=$HOME/go/src/github.com/<your_github_userid>
    export PATH=$GOPATH/bin:$GOROOT/bin:$PATH
    ```

    - Save and exit (`esc : ,wq`)
    - Source the configuration (`source ~/.bashrc`)
- `echo $GOROOT $GOPATH $PATH` (Verifies Go environment variables)
- `go version` (Verifies Go installation)

3. Install Hyperledger Fabric:

- Navigate to your Go project directory (e.g., `cd $HOME/go/src/github.com/<your_github_userid>`)
- Download and set permissions for the installation script:
    - `curl -sSLO https://raw.githubusercontent.com/hyperledger/fabric/main/scripts/install-fabric.sh && chmod +x install-fabric.sh`
- Download Fabric components (choose one):
    - `./install-fabric.sh docker samples binary` (Downloads all components)
        - `docker` - Downloads Fabric container images
        - `samples` - Downloads Fabric samples
        - `binary` - Downloads Fabric binaries

4. Run a Test Network (Optional):

- Navigate to the test-network directory:
    - `cd fabric-samples/test-network`
- Create a channel with a CA and couchdb:
    - `./network.sh up createChannel -ca -c mychannel -s couchdb` (Creates channel "mychannel")

5. Deploy a Chaincode (Optional):

- Requires `jq` package (`sudo apt-get install jq`)
- Deploy asset-transfer-basic Go chaincode:
    - `./network.sh deployCC -ccn basic -ccp ../asset-transfer-basic/chaincode-go/ -ccl go` (Deploys chaincode in Go)

6. Bring Down the Network (Optional):

- From the test-network directory:
    - `./network.sh down`

Note: These are the core commands for setting up Hyperledger Fabric. Additional configuration and steps might be needed depending on your specific use case. 


