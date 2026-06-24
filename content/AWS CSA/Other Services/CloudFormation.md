---
link:
  - "[[IaC|IaC]]"
  - "[[AWS]]"
---

It is a declarative way of outlining your AWS infrastructure for all resources.

For example, you can:
- Define a security group
- Create multiple EC2 instances
- Create S3 Buckets
and so on.

> Only the "Resources" section is mandatory.

**Benefits**: 
- IaC
- Cost advantage, estimate costs easier
- Productivity, you dont have to do ordering
- Templates, don't do everything from scratch


## Services Role
CloudFormation needs [[IAM|IAM MAIN]] roles to actually provision resources. However, if you want to give users access to CloudFormation, but not resources itself, you should use *[[IAM Service Role]]*

## Template
It is a YAML or JSON file that acts as a blueprint. It lists resources and how they should be configured.

## Stack
The collection of live, running resources that has been built by templates are called Stack. 

## StackSets
It is the collection of Stacks. You can use the same template to build 50 stacks.

With StackSets, you can create, update, or delete stacks across multiple accounts and regions with a single operation. 