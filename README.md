# asteria

## 1.環境のインストール
### 1)Docker(linux ver)
```
sudo apt install docker.io
```
### 2)kubectl
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
```
これで以下のように応答すればOK。
```
kubectl: OK
```
インストールする環境が整ったので以下を実行する。
```
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
kubectl version --client
```
### 3)helm
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```
### 4)kind
```
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```
### 5)just
```
mkdir -p ~/bin
curl --proto '=https' --tlsv1.2 -sSf https://just.systems/install.sh | bash -s -- --to ~/bin
export PATH="$PATH:$HOME/bin"
```
### 6)foundry
```
curl -L https://foundry.paradigm.xyz | bash
```

## 2.ローカル環境の構築
```
git clone https://github.com/astriaorg/dev-cluster.git
just create-cluster
just deploy-ingress-controller
just wait-for-ingress-controller
just deploy-astria-local
```
## 3.最新のasteriaのダウンロード
```
curl -L https://github.com/astriaorg/astria/releases/download/cli-v0.3.1/astria-cli-x86_64-unknown-linux-gnu.tar.gz > astria-cli.tar.gz
tar -xvzf astria-cli.tar.gz
```
## 4.独自のロールアップの作成
```
./astria-cli rollup config create --rollup.name <name>
```


