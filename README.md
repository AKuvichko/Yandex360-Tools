# Yandex360-Tools
A set of tools for Yandex 360

## Shared Mailbox

A bash script to add a shared mailbox and assign users to it

Created by Alexander Kuvichko [AKuvichko] [amk] 2025-03-20

Launch it from wsl or from a Linux vm

### LICENSE
Feel free to use this script as you want

### Usage
Make sure you did set the following environment variables in either `~/.bashrc` and/or `/etc/environment`:
- `export orgid=....`
- `export oauth360=...`
  - oauth360 should be looking like "OAuth y0_fff<token_data>xxx"

Install `jq` and `curl`

Set mailbox address, its name and its description
- `email="test-xxx@domain.ru"`
- `name="TEST SHARED MAILBOX"`
- `description="TEST SHARED MAILBOX DESCRIPTION"`

Declare the list of aliases separated by spaces
- `declare -a mails=("user1@domain.ru" "user2@domain.ru" "user3@domain.ru")`

Advanced settings:
Set the total number of employees in your organization
- `employeesTotal=1234`
Keep in mind `$employeesTotal` [1234, total org quota foy Y360] <= `$maxpage` * `$perPage` (`$perPage`=100 for stability reasons)
- `perPage=100`
- `maxpage=$(( $employeesTotal / $perPage + 1 ))`
Assigning role is "Mailbox Owner" you may change it as per Y360 documentation
- `role="shared_mailbox_owner"`

### Launch

Make sure the script can be executed
- `chmod +x ./y360-shared-mailbox`
- Launch `./y360-shared-mailbox`
  
