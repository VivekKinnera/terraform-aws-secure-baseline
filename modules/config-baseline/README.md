# config-baseline

Enable AWS Config in all regions to automatically take configuration snapshots.

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 0.13 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 3.50.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | 3.60.0 |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [aws_config_configuration_recorder.recorder](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/config_configuration_recorder) | resource |
| [aws_config_configuration_recorder_status.recorder](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/config_configuration_recorder_status) | resource |
| [aws_config_delivery_channel.bucket](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/config_delivery_channel) | resource |
| [aws_sns_topic.config](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/sns_topic) | resource |
| [aws_sns_topic_policy.config](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/sns_topic_policy) | resource |
| [aws_caller_identity.current](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/caller_identity) | data source |
| [aws_iam_policy_document.config-sns-policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_region.current](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/region) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_delivery_channel_name"></a> [delivery\_channel\_name](#input\_delivery\_channel\_name) | The name of the delivery channel. | `string` | `"default"` | no |
| <a name="input_delivery_frequency"></a> [delivery\_frequency](#input\_delivery\_frequency) | The frequency which AWS Config sends a snapshot into the S3 bucket. | `string` | `"One_Hour"` | no |
| <a name="input_enabled"></a> [enabled](#input\_enabled) | The boolean flag whether this module is enabled or not. No resources are created when set to false. | `bool` | `true` | no |
| <a name="input_iam_role_arn"></a> [iam\_role\_arn](#input\_iam\_role\_arn) | The ARN of the IAM Role which AWS Config will use. | `any` | n/a | yes |
| <a name="input_include_global_resource_types"></a> [include\_global\_resource\_types](#input\_include\_global\_resource\_types) | Specifies whether AWS Config includes all supported types of global resources with the resources that it records. | `bool` | `true` | no |
| <a name="input_recorder_name"></a> [recorder\_name](#input\_recorder\_name) | The name of the configuration recorder. | `string` | `"default"` | no |
| <a name="input_s3_bucket_name"></a> [s3\_bucket\_name](#input\_s3\_bucket\_name) | The name of the S3 bucket which will store configuration snapshots. | `any` | n/a | yes |
| <a name="input_s3_key_prefix"></a> [s3\_key\_prefix](#input\_s3\_key\_prefix) | The prefix for the specified S3 bucket. | `string` | `""` | no |
| <a name="input_sns_topic_kms_master_key_id"></a> [sns\_topic\_kms\_master\_key\_id](#input\_sns\_topic\_kms\_master\_key\_id) | To enable SNS Topic encryption enter value with the ID of a custom master KMS key that is used for encryption | `any` | `null` | no |
| <a name="input_sns_topic_name"></a> [sns\_topic\_name](#input\_sns\_topic\_name) | The name of the SNS Topic to be used to notify configuration changes. | `string` | `"ConfigChanges"` | no |
| <a name="input_tags"></a> [tags](#input\_tags) | Specifies object tags key and value. This applies to all resources created by this module. | `map` | <pre>{<br>  "Terraform": true<br>}</pre> | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_config_sns_topic"></a> [config\_sns\_topic](#output\_config\_sns\_topic) | The SNS topic that AWS Config delivers notifications to. |
| <a name="output_configuration_recorder"></a> [configuration\_recorder](#output\_configuration\_recorder) | The configuration recorder. |
<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
