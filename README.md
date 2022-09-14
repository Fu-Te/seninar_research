# 日本語
# 初めに
本レポジトリは卒論に向けた開発を行うためのものである．

# システムの概要
BLEとBlockchainを組み合わせたシステムを構築する．
Raspberrypiは4台程度用意し，相互通信をBLEを用いて実現する．
RaspberrypiをBLEビーコンとし，スマートフォンやノートパソコンのBLEブロードキャストをキャッチする．キャッチした情報をAESで暗号化し，BLE経由でデバイス間で共有する．共有されたデータをブロックにのせ，以前のハッシュ値と見比べることでチェーンを作成する．

# blockchain
blockchainフォルダでは，ブロックとチェーンを作成し，情報を載せるためのブロックチェーンを実装する．

ブロックチェーンをテストするためのDockerを作成している途中である．


# ble

Raspberrypi同士の通信ではl2cap_client.pyとl2cap_server.pyを利用する．
discover.pyでbleブロードキャストをキャッチする．

raspberrypiのbleではセキュリティの観点からか，ble検索にかからないようになっているので，定期的に以下のコマンドを実行する必要がある.
つまりサーバーとして情報を受け取るためには以下のコマンドを毎回行う必要があるので，サーバを起動するときに以下のコマンドを自動的に実行するように変更する必要がある．
```
$ bluetoothctl
$ discoverable on
```


#　環境構築
Raspberrypi上で
```
$ sudo apt-get install git
$ git clone https://github.com/Fu-Te/BLE_Blockchain
$ cd BLE_Blockchain
$ sudo apt-get install libatlas-base-dev
$ sudo apt-get install libjasper-dev
$ sudo apt-get install bluetooth libbluetooth-dev
$ pip install -r requirements.txt
```
上記コマンドを行なうと環境構築が完了する．

# 使い方
```
$ python3 main.py
```
上記コマンドを実行することで利用することが可能．

# pytest
pytestを用いたテストを考えている