



<h1>Install Docker</h1>

```console
sudo apt update -y && sudo apt upgrade -y

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Docker version check
docker --version
```

<h1>Pull docker mirroring</h1>

```console
docker pull privasea/acceleration-node-beta:latest
```

<h1>Node program configuration</h1>

```console
mkdir -p ~/privasea/config && cd ~/privasea
```

<h1>Get the keystore file</h1>

```console
docker run --rm -it -v "$HOME/privasea/config:/app/config" privasea/acceleration-node-beta:latest ./node-calc new_keystore
```
<h1>NOTE:</h1>

The program will prompt you to enter a password, please remember this password for future use.

![-218677_temp](https://github.com/user-attachments/assets/0efcbf96-407f-46db-9f27-a0fcc4c0817e)

🔹You should save your node address, it will be useful later

🔹Save data from UTC--2025 till the end [Check SS for more clearity]

<h1>Change the ➕ to UTC file name you saved above</h1>

```console
mv $HOME/privasea/config/+ $HOME/privasea/config/wallet_keystore
```
<h1>Update your password before starting the node</h1>

```console
KEYSTORE_PASSWORD=ENTER_YOUR_KEYSTORE_PASSWORD && docker run -d --name privanetix-node -v "$HOME/privasea/config:/app/config" -e KEYSTORE_PASSWORD=$KEYSTORE_PASSWORD privasea/acceleration-node-beta:latest
```
<h1>Check Node Logs</h1>

```console
docker logs -f privanetix-node
```
<h1>Link node address and reward address</h1>

Link: https://deepsea-beta.privasea.ai/privanetixNode

![image](https://github.com/user-attachments/assets/f4e5dfee-b065-4bd8-9174-716cd661e2d2)
