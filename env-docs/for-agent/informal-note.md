# Example Informal Environment Doc Note

This environment is a home server on Daniel's LAN. He might call it simply "Ubuntu VM".

It's authenticated via SSH with other devices on the LAN. So if Daniel asks you to pull in files from it Or export them try using ssh. You should not face password prompts.

## Purpose

This machine has a few purposes:

1: It hosts a docker environment with a few sytstems that Daniel uses 
2: It is a backup runner: it hosts backup scripts and stores data, some of which is synced to clouds

## Filesystem Organisation

Daniel likes to distinguish clearly between the two purposes of the system so 'docker-network' and 'backups' are the top level entities. 

## Backup Data Vs. Code

Daniel's general approach is this:

- Backup scripts are written 
- They are versioned on Github
- They are deployed to this server 

They are written to target storage directories outside of the repo and/or on remotes and/or on the local NAS. Make sure that any backup repo you encounter follows this model. If it doesn't, refactor it and then push that update to Github (assume auth via GH in place)