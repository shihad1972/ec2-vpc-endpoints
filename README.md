ec2-vpc-endpoint
=========

Create endpoints within an AWS VPC.

Requirements
------------

Boto is required for this module.

Role Variables
--------------

ec2_gw_endpoints: A list of the gateway type endpoints to create. The only
                  2 types are s3 and DynamoDB
ec2_if_endpoints: A list of the interface type endpoints to create.
sec_group_names: A list of security groups to attach to an interface type
                 endpoint.
subnet_names: A list of subnet names that will have the interface endpoint
              type created in.
             

Dependencies
------------

There are no dependencies for this role.

Example Playbook
----------------

    - hosts: localhost
      vars:
        region: eu-west-1
        ec2_endpoints:
          - "com.amazonaws.{{ region }}.ec2"
        sec_group_names:
          - VPC Endpoints
        subnet_names:
          - Application Private a
          - Application Private b
      roles:
         - { role: ec2-vpc-endpoint,
               ec2_if_endpoints: "{{ ec2_endpoints }}",
               sec_group_names: "{{ ec2_security_groups }}",
               subnet_names: "{{ ec2_subnets }}" }

License
-------

GPLv3

Author Information
------------------

Iain M Conochie <iain-at-thargoid-dot-co-dot-uk>
