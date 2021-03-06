---
layout: "aws"
page_title: "AWS: aws_appautoscaling_target"
sidebar_current: "docs-aws-resource-appautoscaling-target"
description: |-
  Provides an Application AutoScaling ScalableTarget resource.
---

# aws\_appautoscaling\_target

Provides an Application AutoScaling ScalableTarget resource.

## Example Usage
```
resource "aws_appautoscaling_target" "ecs_target" {
  max_capacity = 4
  min_capacity = 1
  resource_id = "service/clusterName/serviceName"
  role_arn = "${var.ecs_iam_role}"
  scalable_dimension = "ecs:service:DesiredCount"
  service_namespace = "ecs"
}
```

## Argument Reference

The following arguments are supported:

* `max_capacity` - (Required) The max capacity of the scalable target.
* `min_capacity` - (Required) The min capacity of the scalable target.
* `resource_id` - (Required) The resource type and unique identifier string for the resource associated with the scalable target. For Amazon ECS services, this value is the resource type, followed by the cluster name and service name, such as `service/default/sample-webapp`. For Amazon EC2 Spot fleet requests, the resource type is `spot-fleet-request`, and the identifier is the Spot fleet request ID; for example, `spot-fleet-request/sfr-73fbd2ce-aa30-494c-8788-1cee4EXAMPLE`.
* `role_arn` - (Required) The ARN of the IAM role that allows Application AutoScaling to modify your scalable target on your behalf.
* `scalable_dimension` - (Required) The scalable dimension of the scalable target. The scalable dimension contains the service namespace,   resource  type, and scaling property, such as `ecs:service:DesiredCount` for the desired task count of an Amazon ECS service, or `ec2:spot-fleet-request:TargetCapacity` for the target capacity of an Amazon EC2 Spot fleet request.
* `service_namespace` - (Required) The AWS service namespace of the scalable target. Valid values are `ecs` for Amazon ECS services and `ec2` Amazon EC2 Spot fleet requests.
