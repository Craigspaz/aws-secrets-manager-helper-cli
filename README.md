# Sekrit

| A very simple command-line tool for interacting with AWS Secrets Manager

## Installing

Put `sekrit` somewhere in your path.

## Usage

Ensure that you have [correctly configured the AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html) and have selected a profile if needed.

```console
sekrit [ls|get <name>|set <name> <value>|rm <name>|restore <name>]
```

## Example invocations

**Set or update a secret:** Sekrit outputs the value to confirm that it has been set correctly.

```console
$ sekrit set cake lie
lie
```

**Get a secret:**

```console
$ sekrit get cake
lie
```

**List all secrets:**

```console
$ sekrit ls
cake
```

**Remove a secret:** Sekrit outputs the secret's value when deleting it. By default, secrets can be restored for up to 30 days after deletion.

```console
$ sekrit rm cake
lie
```

**Restore a deleted secret:** Sekrit outputs the secret's value after restoring it.

```console
$ sekrit restore cake
lie
```

## Limitations

Sekrit does not check that you have permissions to perform the actions you request and will exit with an error message from the AWS CLI if something goes wrong.

Sekrit does not attempt to process the value stored in secretsmanager so you will need to pipe out to another tool to parse a JSON secret value, for example.
