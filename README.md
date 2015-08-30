# ansible

## インストール

```bash
$ brew install ansible
```

## 設定

```bash
$ cat hosts
[vagrant]
default
```

## ディレクトリ構成

```bash
.
├── README.md
├── Vagrantfile
├── ansible.cfg
├── filter_plugins
├── group_vars
│   ├── pubkeys
│   │   ├── id_rsa.pub.alice
│   │   ├── id_rsa.pub.bob
│   │   └── id_rsa.pub.john
│   └── users.yml
├── host_vars
├── hosts
├── library
├── roles
│   └── base
│       ├── defaults
│       ├── files
│       ├── handlers
│       ├── meta
│       ├── tasks
│       │   ├── main.yml
│       │   ├── rpms.yml
│       │   └── users.yml
│       ├── templates
│       └── vars
├── ssh-config
└── vagrant.yml
```

## 問題点

* 全体のアカウント情報をまとめて管理しつつ、roleに応じて展開するアカウントを分けること

## テスト

```bash
$ ansible vagrant -i hosts -m ping
default | success >> {
    "changed": false,
    "ping": "pong"
}
```

ansible-playbook時にこんなエラーが出た

```bash
msg: Aborting, target uses selinux but python bindings (libselinux-python) aren't installed!
```

参考

* [Ansible GalaxyにGitBucketのroleを登録した - 三角Validator](http://sankakuvalidator.hatenablog.com/entry/ansible-role-gitbucket)


## コマンド

[Ansible サーバ管理メモ - Qiita](http://qiita.com/Machi427/items/b3c0ed5f8a2cd3a8236e)

* 文法チェック  
`$ ansible-playbook playbook/servers_local.yml --syntax-check`

* 対象ホストを確認する  
`$ ansible-playbook playbook/servers_local.yml --list-hosts`

* 対象タスクを確認する
`$ ansible-playbook playbook/servers_local.yml --list-task`

* Dry run  
`$ ansible-playbook playbook/servers_local.yml --check`

* step 実行  
`$ ansible-playbook playbook/servers_local.yml --step`

* ホスト指定実行  
`$ansible-playbook playbook/servers_local.yml -l [hostname]`

* タグ指定実行  
`$ ansible-playbook playbook/servers_local.yml --tags=XXX`

* 接続テスト (インベントリやホストの切り替え後に接続テストする）  
`$ ansible-playbook playbook/ping.yml`


## 参考リンク

* [Ansible の authorized_key モジュールで lookup プラグインを使う時にユーザー名を変数で指定](http://fishrimper.blogspot.jp/2015/04/ansible-authorizedkey-lookup.html)
* http://www.bbreak.co.jp/technique/doc/ansible/Ansible.pdf
* [Ansible Tower | Ansible.com](http://www.ansible.com/tower?utm_source=docs)
* [Ansible オレオレベストプラクティス - Qiita](http://qiita.com/yteraoka/items/5ed2bddefff32e1b9faf#2-1)
* [Ansibleのincludeとroles機能 | OpenGroove](http://open-groove.net/ansible/include-roles/)
* [RolesでAnsibleのPlaybookを整理してみよう|株式会社INDETAIL（札幌/東京）（iPhone/iPad/iOS/Android)](http://www.indetail.co.jp/blog/ansible-2/)
* [AnsibleのUserモジュールでpasswordを設定する時の注意 - a long log](http://longkey1.net/blog/2014/01/22/ansible-add-user-password/)
* [1Q77 | Ansible でユーザーを一括作成する](https://blog.1q77.com/2013/08/create-user-using-ansible/)


## ユーザ管理で参考になりそうなリポジトリ

* https://github.com/debops/ansible-users
* https://github.com/mivok/ansible-users

