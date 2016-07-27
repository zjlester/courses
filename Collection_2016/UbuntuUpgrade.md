#命令行升级Ubuntu发行版

```bash
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install update-manager-core
sudo vim /etc/update-manager/release-upgrades
修改 Prompt=lts => normal


sudo do-release-upgrade -d
显示：
Checking for a new Ubuntu release
