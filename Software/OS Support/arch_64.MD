### Convert from .deb
`debtap -p pijuice-base_1.8_all.deb`

### Then apply fixes to .INSTALL for arch.
- adduser to useradd+gpasswd
  ```
  echo "Creating user pijuice"
  useradd --shell /usr/bin/false --home-dir /var/lib/pijuice pijuice
  gpasswd -a pijuice i2c
  # Add default user (usually pi) to the pijuice group
  defuser=`id -un 1000`
  gpasswd -a $defuser pijuice
  ```
- dist-packages to site-packages (`python -m site`)
- python 3.9 to python 3.10 (`python -m site`)

### Repackage

### Install
`pacman -U pijuice-base-1.8-1-any-fix.pkg.tar`
