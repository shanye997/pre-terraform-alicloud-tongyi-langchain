阿里云通义千问和 LangChain 对话服务 Terraform 模块

================================================ 

# terraform-alicloud-tongyi-langchain

[English](https://github.com/alibabacloud-automation/terraform-alicloud-tongyi-langchain/blob/main/README.md) | 简体中文

在阿里云上创建完整的通义千问和 LangChain 对话服务基础设施的 Terraform 模块。该模块实现了[通义千问和 LangChain 搭建对话服务](https://www.aliyun.com/solution/tech-solution/tongyi-langchain)解决方案，涉及 PAI-EAS、专有网络（VPC）、交换机（VSwitch）和文件存储 NAS 等资源的创建和部署。

## 使用方法

该模块创建一个完整的 AI 对话服务基础设施，包括 PAI-EAS 服务、网络组件和文件存储。您可以使用此模块快速部署基于通义千问和 LangChain 的生产级对话服务。

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

## 示例

* [完整示例](https://github.com/alibabacloud-automation/terraform-alicloud-tongyi-langchain/tree/main/examples/complete)

<!-- BEGIN_TF_DOCS -->
<!-- END_TF_DOCS -->

## 提交问题

如果您在使用此模块时遇到任何问题，请提交一个 [provider issue](https://github.com/aliyun/terraform-provider-alicloud/issues/new) 并告知我们。

**注意：** 不建议在此仓库中提交问题。

## 作者

由阿里云 Terraform 团队创建和维护(terraform@alibabacloud.com)。

## 许可证

MIT 许可。有关完整详细信息，请参阅 LICENSE。

## 参考

* [Terraform-Provider-Alicloud Github](https://github.com/aliyun/terraform-provider-alicloud)
* [Terraform-Provider-Alicloud Release](https://releases.hashicorp.com/terraform-provider-alicloud/)
* [Terraform-Provider-Alicloud Docs](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs)