Example inventory:

```yaml
openshift:
  hosts:
    localhost:
      ansible_connection: local
  vars:
    admin_user: <user>
    admin_password: <password>
    aws:
      aws_access_key_id: <key>
      aws_secret_access_key: <key>
      aws_region: us-east-2
    ocp_cluster:
      name: demo-cluster
      base_domain: example.com
      ocp_version: 4.18
    install_config:
      cluster_name: "{{ ocp_cluster.name }}"
      base_domain: "{{ ocp_cluster.base_domain }}"
      aws_region: "{{ aws.aws_region }}"
      control_plane:
        instance_type: "m5.xlarge"
      workers:
        instance_type: "m5.2xlarge"
        replicas: "3"
      infras:
        instance_type: "m5.2xlarge"
      pull_secret: '{"auths":{"cloud.openshift.com":<... SNIP ...>}'
```