# Complete Example

This example demonstrates the complete usage of the Tongyi-LangChain Terraform module. It creates all the necessary resources for building a conversation service with Qwen and LangChain, including VPC, VSwitch, security group, NAS file system, and PAI-EAS service.

## Usage

To run this example, you need to execute:

```bash
$ terraform init
$ terraform plan
$ terraform apply
```

Note that this example will create resources that may cost money. Run `terraform destroy` when you don't need these resources.

## Requirements

| Name | Version |
|------|---------|
| terraform | >= 1.0 |
| alicloud | >= 1.200.0 |

## Providers

| Name | Version |
|------|---------|
| alicloud | >= 1.200.0 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| tongyi_langchain | ../../ | n/a |

## Resources

| Name | Type |
|------|------|
| [alicloud_zones.available](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs/data-sources/zones) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| region | The region where to deploy the resources | `string` | `"cn-hangzhou"` | no |
| common_name_prefix | Common name prefix for all resources | `string` | `"tongyi-langchain-example"` | no |
| vpc_cidr_block | CIDR block for the VPC | `string` | `"192.168.0.0/16"` | no |
| zone_id | The zone ID where to deploy the resources. If not specified, will use the first available zone | `string` | `null` | no |
| pai_instance_type | Instance type for PAI-EAS service | `string` | `"ml.gu7i.c8m30.1-gu30"` | no |

## Outputs

| Name | Description |
|------|-------------|
| vpc_id | The ID of the VPC |
| pai_service_id | The ID of the PAI-EAS service |
| service_name | The name of the PAI-EAS service |
| service_status | The status of the PAI-EAS service |

## Notes

- Make sure you have the necessary permissions to create PAI-EAS services in your Alibaba Cloud account
- The PAI-EAS service creation may take several minutes to complete
- Ensure the selected zone supports the instance type you want to use
- The default configuration creates a basic setup suitable for testing and development