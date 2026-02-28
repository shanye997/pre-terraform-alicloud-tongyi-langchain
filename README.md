Alibaba Cloud Tongyi Qwen and LangChain Conversation Service Terraform Module

================================================ 

# terraform-alicloud-tongyi-langchain

English | [简体中文](https://github.com/alibabacloud-automation/terraform-alicloud-tongyi-langchain/blob/main/README-CN.md)

Terraform module which creates a complete conversation service infrastructure with Tongyi Qwen and LangChain on Alibaba Cloud. This module implements the solution for [Building a conversation service with Qwen and LangChain](https://www.aliyun.com/solution/tech-solution/tongyi-langchain), which involves the creation and deployment of resources such as PAI-EAS, Virtual Private Cloud (VPC), VSwitch, and File Storage NAS.

## Usage

This module creates a comprehensive AI conversation service infrastructure including PAI-EAS service, networking components, and file storage. You can use this module to quickly deploy a production-ready conversation service based on Tongyi Qwen and LangChain.

```terraform
module "tongyi_langchain" {
  source = "alibabacloud-automation/tongyi-langchain/alicloud"

  common_name_prefix = "my-ai-service"

  vpc_config = {
    cidr_block = "192.168.0.0/16"
    vpc_name   = "tongyi-vpc"
  }

  vswitch_config = {
    zone_id      = "cn-hangzhou-f"
    cidr_block   = "192.168.0.0/24"
    vswitch_name = "tongyi-vswitch"
  }

  pai_service_config = {
    instance_type = "ml.gu7i.c8m30.1-gu30"
    cpu           = 8
    gpu           = 1
    memory        = 30000
  }
}
```

## Examples

* [Complete Example](https://github.com/alibabacloud-automation/terraform-alicloud-tongyi-langchain/tree/main/examples/complete)

<!-- BEGIN_TF_DOCS -->
<!-- END_TF_DOCS -->

## Submit Issues

If you have any problems when using this module, please opening
a [provider issue](https://github.com/aliyun/terraform-provider-alicloud/issues/new) and let us know.

**Note:** There does not recommend opening an issue on this repo.

## Authors

Created and maintained by Alibaba Cloud Terraform Team(terraform@alibabacloud.com).

## License

MIT Licensed. See LICENSE for full details.

## Reference

* [Terraform-Provider-Alicloud Github](https://github.com/aliyun/terraform-provider-alicloud)
* [Terraform-Provider-Alicloud Release](https://releases.hashicorp.com/terraform-provider-alicloud/)
* [Terraform-Provider-Alicloud Docs](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs)