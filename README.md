# ansible

## tree

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

## やりたいけどできてないこと

* 全体のアカウント情報をまとめて管理しつつ、roleに応じて展開するアカウントを分けること
