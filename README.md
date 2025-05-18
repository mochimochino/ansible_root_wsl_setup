## Ansibleを用いたROOT環境の構築
[ROOT公式](https://root.cern/install/)をもとに必要なパッケージをインストールし、環境構築を行う。
### 事前準備
epelのインストールと、Ansibleのインストールを行う。
```
sudo dnf install -y epel-release
```
```
sudo dnf install -y ansible python3-pip
```
### Playbookの実行方法
- Playbookを配置したディレクトリへの移動
```
cd ~/ansible-root-wsl-setup
```
- Ansible Playbookの実行
```
ansible-playbook -i inventory.ini playbook.yml -K
``` 
(詳細なログを表示したい場合は-vをつけて実行する。）

### ディレクトリの構成
```
ansible-root-wsl-setup/
├── playbook.yml                # メインのPlaybookファイル
├── inventory.ini               # 対象ホスト (WSL AlmaLinux 9) を定義
├── vars/
│   └── wsl_almalinux_vars.yml  # WSL AlmaLinux 9用の変数を定義
└── roles/
     ├── wsl_almalinux_setup/      # リポジトリ設定と依存パッケージインストール
    │   └── tasks/
    │       └── main.yml
    └── root_install_binary/      # ROOTバイナリのダウンロード、展開、環境設定
        └── tasks/
            └── main.yml
```
