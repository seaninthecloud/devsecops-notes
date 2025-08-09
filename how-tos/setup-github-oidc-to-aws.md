# Setup GitHub OIDC to AWS (notes)
1) Create IAM role with GitHub OIDC as federated principal.
2) Trust policy `sub` pattern: `repo:ORG/REPO:*`.
3) In Actions, use `aws-actions/configure-aws-credentials` with that role.