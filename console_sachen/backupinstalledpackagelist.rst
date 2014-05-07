#create a list of installed packages for easier restore after a system fail/reinstall

for infos on installed packages and how to restore them:
http://askubuntu.com/questions/9135/best-way-to-backup-all-settings-list-of-installed-packages-tweaks-etc



mkdir /var/backups/installedpackages
dpkg --get-selections > /var/backups/installedpackages/package.list
cp -R /etc/apt/sources.list* /var/backups/installedpackages
apt-key exportall > /var/backups/installedpackages/repo.keys



