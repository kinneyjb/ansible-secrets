# ansible-secrets

*note:* this is just an example...

example of using ansible to:
* generate private keys
* create vaults using encryp_string
* loop through vaulted values

## running

This example requires that you have a the `ANSIBLE_VAULT_PASSWORD_FILE` set in your environment.
Included in this example is a `vault_pass.txt` which can be used, dont really commit this to scm.

```bash
$ echo $SHELL
/bin/bash

$ export ANSIBLE_VAULT_PASSWORD_FILE=vault_pass.txt
$ ansible-playbook secrets.yml
```

Which generates:
* 2 keypairs in `generated/secrets`
* 1 dictionary in `generated/vaults/vaulted-keys.yml`
	* key: name of the keypair
	* value: encrypted value of the private key (using `ansible-vault encrypt_string`)

```
generated/
├── secrets
│   ├── private1
│   ├── private1.pub
│   ├── private2
│   └── private2.pub
└── vaults
    └── vaulted-keys.yml

2 directories, 5 files

```
