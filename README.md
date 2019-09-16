# packer-base
> simple packer example 

## requirements

  - `packer @ >= 1.4.3`

 - creates ami w/ all of the necessary software
 - speeds up boot times of instances
 - common approach when you run a horizontally scaled app layer

Build custom ami, `test_ami`:
```sh
cd packer/test_ami
packer build -machine-readable packer.json
```

Add aws default region to `.profile` or `.zprofile`:
```sh
export AWS_DEFAULT_REGION=us-west-2
```

Created script to list and delete user amis (requires `awscli`):
```sh
Usage: ./aws_ami_cleaner.sh [options]

Options:

  -a, --aws_account_id <id>  aws account id
  -l, --list                 list user amis
  -d, --delete_all           delete all user amis
  -h, --help                 output usage information
```

How to use the script:
```sh
# list user amis
./aws_ami_cleaner.sh -a <aws_account_id> -l

# delete all user amis
./aws_ami_cleaner.sh -a <aws_account_id> -d
```
