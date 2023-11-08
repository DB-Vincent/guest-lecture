# Kubeconform

Kubeconform is a Kubernetes configuration validator that checks your Kubernetes resource configuration files against the Kubernetes API schema to ensure they adhere to best practices and are correctly formatted. It helps users catch potential issues and ensure that their Kubernetes configurations are compliant with the Kubernetes API, promoting reliability and consistency in their deployments.

The tool can be installed as follows:
- Linux and macOS: `brew install kubeconform`
- Windows: `winget install YannHamon.kubeconform`

## Usage

Validating a single, valid file

```shell
$ kubeconform fixtures/valid.yaml
$ echo $?
0
```

Validating a single invalid file, setting output to json, and printing a summary

```shell
$ kubeconform -summary -output json fixtures/invalid.yaml
{
  "resources": [
    {
      "filename": "fixtures/invalid.yaml",
      "kind": "ReplicationController",
      "version": "v1",
      "status": "INVALID",
      "msg": "Additional property templates is not allowed - Invalid type. Expected: [integer,null], given: string"
    }
  ],
  "summary": {
    "valid": 0,
    "invalid": 1,
    "errors": 0,
    "skipped": 0
  }
}
$ echo $?
1
```

Passing manifests via Stdin

```shell
cat fixtures/valid.yaml  | ./bin/kubeconform -summary
Summary: 1 resource found parsing stdin - Valid: 1, Invalid: 0, Errors: 0 Skipped: 0
```

Validating a file, ignoring its resource using both Kind, and GVK (Group, Version, Kind) notations

```shell
# This will ignore ReplicationController for all apiVersions
$ kubeconform -summary -skip ReplicationController fixtures/valid.yaml
Summary: 1 resource found in 1 file - Valid: 0, Invalid: 0, Errors: 0, Skipped: 1

# This will ignore ReplicationController only for apiVersion v1
$ kubeconform -summary -skip v1/ReplicationController fixtures/valid.yaml
Summary: 1 resource found in 1 file - Valid: 0, Invalid: 0, Errors: 0, Skipped: 1
```

Validating a folder, increasing the number of parallel workers

```shell
$ kubeconform -summary -n 16 fixtures
fixtures/crd_schema.yaml - CustomResourceDefinition trainingjobs.sagemaker.aws.amazon.com failed validation: could not find schema for CustomResourceDefinition
fixtures/invalid.yaml - ReplicationController bob is invalid: Invalid type. Expected: [integer,null], given: string
[...]
Summary: 65 resources found in 34 files - Valid: 55, Invalid: 2, Errors: 8 Skipped: 0
```


## More information

[https://github.com/yannh/kubeconform](https://github.com/yannh/kubeconform)
