# EC2 Custom Shared Folder

## Create shared folder

```bash
  # create shared folder
  sudo mkdir -p /opt/shared/repos
  
  # create group
  sudo groupadd dev

  # Add default ec2 user (ec2-user) to dev group
  sudo usermod -aG dev ec2-user

  # Group owner -> dev group 
  sudo chown -R :dev /opt/shared/repos
  # Group access -> read/write/execute 
  sudo chmod -R g+rwX /opt/shared/repos
  # Inherit ownership for all or new files/folders 
  sudo find /opt/shared/repos -type d -exec chmod g+s {} \;

  # Grant git access for the folder
  sudo git config --system --add safe.directory /opt/shared/repos/*
```

## Clone repo

```bash
  cd /opt/shared/repos
  sudo git clone <repo_url>
```
