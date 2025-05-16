## Ansibleを用いたROOT環境の構築
### ディレクトリの構成
```
ansible-root-wsl-setup/
├── playbook.yml                # メインのPlaybookファイル
├── inventory.ini               # 対象ホスト (WSL AlmaLinux 9) を定義
├── vars/
│   └── wsl_almalinux_vars.yml  # WSL AlmaLinux 9用の変数を定義
└── roles/
    ├── common_prerequisites/     # 共通の前提条件 (ディレクトリ作成など)
    │   └── tasks/
    │       └── main.yml
    ├── wsl_almalinux_setup/      # WSL AlmaLinux 9固有のパッケージインストールなど
    │   └── tasks/
    │       └── main.yml
    └── root_build/               # ROOTのダウンロード、ビルド、インストール
        └── tasks/
            └── main.yml
```

