# Ansible Playbooks: wait-for-openshift

![MIT](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)
![GitHub last commit](https://img.shields.io/github/last-commit/gepaplexx/playbook-wait-for-openshift?style=flat-square)
![Maintenance](https://img.shields.io/maintenance/yes/2022?style=flat-square)

## Wait for bootstrap completion

During the openshift installation procedure it is necessary to approve new nodes. This approval process requires the openshift api to be up and running. 

With the `wait-for-bootstrap-complete.yml` playbook we are able to wait until the api is available. Once the bootstrap process is complete we can execute the next step in our installation procedure: the approval of new nodes.

| Variable | Default | Comment |
| :--- | :--- | :--- |
| `ocp_base_path` | | The path to store openshift related data such as install config and openshift-install binary. |
| `ocp_config_path` |  | Install config directory used during openshift installation and configuration. The config directory contains the iginition files created by openshift-install and the initial auth credentials for openshift. |
| `timeout_in_sec` | 3060 | maximal time a long running task is allowed to run before it times out. the "openshift-install wait-for bootstrap-complete" command runs up to 50 minutes before it fails. Hence the timout for the async task is set slightly longer: 51 minutes. |
| `timeout_retry_interval_in_sec` | 30 | interval in which ansible checks if the long runnig tasks has finished. |

## Wait for install completion

Once all nodes have been approved openshift start to rollout its kubernetes resources on the nodes. During this openshift instantiates components such as the registry and the web console among others. While those core componets are beeing deployed we can not reliably continue with any automation process within openshift. Hence the `wait-for-install-complete.yml` playbook.

The `wait-for-install-complete.yml` playbook waits until all core components of openshift have been deployed.

 Variable | Default | Comment |
| :--- | :--- | :--- |
| `ocp_base_path` | | The path to store openshift related data such as install config and openshift-install binary. |
| `ocp_config_path` |  | Install config directory used during openshift installation and configuration. The config directory contains the iginition files created by openshift-install and the initial auth credentials for openshift. |
| `timeout_in_sec` | 3060 | maximal time a long running task is allowed to run before it times out. the "openshift-install wait-for install-complete" command runs up to 50 minutes before it fails. Hence the timout for the async task is set slightly longer: 51 minutes. |
| `timeout_retry_interval_in_sec` | 30 | interval in which ansible checks if the long runnig tasks has finished. |

## License

MIT

## Contributions

- [@ckaserer](https://github.com/ckaserer)
