# Ceph Infrastructure Heat Template
Set of heat templates used to layout the underlying server infrastructure that can be used to build a reasonable multi-node ceph deployment to include several OSDs as well as Monitor servers as a proof of concept. Currently, this does not install Ceph for you. This deployment is intended to be executed using Rackspace Orchestration in the Rackspace Public Cloud. Manual modification is needed to utilize in a standalone OpenStack Heat environment.

## Current Build Specs
* Build anywhere from 1-6 Ceph Monitor Servers with anywhere from 1-4 Cinder Volumes attached (SATA or SSD)
* Build anywhere from 1-8 Ceph OSD servers with anywhere from 1-8 Cinder Volumes attached (SATA or SSD)
* Ubuntu 14.04 or CentOS 7
* One Cloud Network to serve as backend network for whatever purpose.

## Utilizing the templates
Create a custom template in the Rackspace Orchestration Engine and place [main.yaml](https://raw.githubusercontent.com/Komish/heat-templates/master/ceph-infrastructure/main.yaml) as your template. This template will call the subtemplate [serverbuild.yaml](https://raw.githubusercontent.com/Komish/heat-templates/master/ceph-infrastructure/serverbuild.yaml) and [volumeattachment.yaml](https://raw.githubusercontent.com/Komish/heat-templates/master/ceph-infrastructure/volumeattachment.yaml) for easier reusability of tasks. 

## Todolist
- [ ] Implement Rados Gateway infrastructure considerations
- [ ] Integrate Client servers for additional testing.

## Current Issues
* This deployment in the Rackspace Orchestration engine does not properly identify all resources once the build is completed. This is a result of the state of those resources being returned as 'CREATE_IN_PROGRESS' despite being fully deployed. 
