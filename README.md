## Requirements

No requirements.

## Providers

| Name | Version |
|------|---------|
| <a name="provider_archive"></a> [archive](#provider\_archive) | n/a |
| <a name="provider_aws"></a> [aws](#provider\_aws) | n/a |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [aws_cloudwatch_event_rule.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/cloudwatch_event_rule) | resource |
| [aws_cloudwatch_event_target.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/cloudwatch_event_target) | resource |
| [aws_cloudwatch_log_group.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/cloudwatch_log_group) | resource |
| [aws_iam_policy.additional_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_policy) | resource |
| [aws_iam_policy.lambda_eni](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_policy) | resource |
| [aws_iam_policy.lambda_logging](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_policy) | resource |
| [aws_iam_policy.lambda_warmer](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_policy) | resource |
| [aws_iam_policy.lambda_xray](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_policy) | resource |
| [aws_iam_role.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role) | resource |
| [aws_iam_role_policy_attachment.additional_permissions](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |
| [aws_iam_role_policy_attachment.lambda_eni](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |
| [aws_iam_role_policy_attachment.lambda_logs](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |
| [aws_iam_role_policy_attachment.lambda_warmer](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |
| [aws_iam_role_policy_attachment.lambda_xray](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |
| [aws_lambda_function.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/lambda_function) | resource |
| [aws_lambda_permission.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/lambda_permission) | resource |
| [aws_security_group.lambda_sg](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group) | resource |
| [aws_security_group_rule.lambda_sgr_egress](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group_rule) | resource |
| [aws_security_group_rule.lambda_sgr_ingress](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group_rule) | resource |
| [archive_file.lambda_app](https://registry.terraform.io/providers/hashicorp/archive/latest/docs/data-sources/file) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_additional_lambda_policy"></a> [additional\_lambda\_policy](#input\_additional\_lambda\_policy) | Additional permissions for the Lambda function, as policy document. | `string` | `null` | no |
| <a name="input_architectures"></a> [architectures](#input\_architectures) | Lambda architectures. Valid values are ["x86\_64"] and ["arm64"] | `list(string)` | <pre>[<br>  "arm64"<br>]</pre> | no |
| <a name="input_create_version"></a> [create\_version](#input\_create\_version) | Create a Lambda version on change? | `bool` | `true` | no |
| <a name="input_default_security_group_id"></a> [default\_security\_group\_id](#input\_default\_security\_group\_id) | Default security group ID of the VPC | `list(string)` | `[]` | no |
| <a name="input_enable_xray"></a> [enable\_xray](#input\_enable\_xray) | Enable Xray tracing. | `bool` | `false` | no |
| <a name="input_environment_variables"></a> [environment\_variables](#input\_environment\_variables) | Environment variables. | <pre>list(object({<br>    variables = map(string)<br>  }))</pre> | `[]` | no |
| <a name="input_keep_warm"></a> [keep\_warm](#input\_keep\_warm) | Keeps the Lambda warm and prevents cold starts. | `bool` | `false` | no |
| <a name="input_keep_warm_options"></a> [keep\_warm\_options](#input\_keep\_warm\_options) | Options for the Lambda warmer. | <pre>object({<br>    rate  = string<br>    input = string<br>  })</pre> | `null` | no |
| <a name="input_lambda_layers"></a> [lambda\_layers](#input\_lambda\_layers) | Layers that are used by the Lambda function | `list(string)` | `[]` | no |
| <a name="input_lambda_name"></a> [lambda\_name](#input\_lambda\_name) | Name of the lambda function. | `string` | n/a | yes |
| <a name="input_log_retention"></a> [log\_retention](#input\_log\_retention) | Lambda log retention in days. | `number` | `7` | no |
| <a name="input_memory_size"></a> [memory\_size](#input\_memory\_size) | Maximum memory size of the Lambda function. | `number` | `128` | no |
| <a name="input_project"></a> [project](#input\_project) | Project name. | `string` | n/a | yes |
| <a name="input_region"></a> [region](#input\_region) | Name of the current region. | `string` | `"eu-central-1"` | no |
| <a name="input_runtime"></a> [runtime](#input\_runtime) | Runtime of the Lambda function. | `string` | `"nodejs14.x"` | no |
| <a name="input_security_group_configuration"></a> [security\_group\_configuration](#input\_security\_group\_configuration) | Security group configuration for the Lambda function. | <pre>object({<br>    vpc_id = string<br>    ingress = object({<br>      from_port   = number<br>      to_port     = number<br>      protocol    = string<br>      cidr_blocks = list(string)<br>    })<br>    egress = object({<br>      from_port   = number<br>      to_port     = number<br>      protocol    = string<br>      cidr_blocks = list(string)<br>    })<br>  })</pre> | `null` | no |
| <a name="input_source_dir"></a> [source\_dir](#input\_source\_dir) | Source dir of the Lambda code. | `string` | n/a | yes |
| <a name="input_stage"></a> [stage](#input\_stage) | Name of the stage. | `string` | n/a | yes |
| <a name="input_subnet_ids"></a> [subnet\_ids](#input\_subnet\_ids) | List of subnet ID's to deploy the Lambda function. | `list(string)` | `[]` | no |
| <a name="input_timeout"></a> [timeout](#input\_timeout) | Timeout in seconds of the Lambda function. | `number` | `3` | no |

## Outputs

| Name | Description                        |
|------|------------------------------------|
| <a name="output_function_arn"></a> [function\_arn](#output\_function\_arn) | The ARN of the Lambda function     |
| <a name="output_function_name"></a> [function\_name](#output\_function\_name) | The name of of the Lambda function |
