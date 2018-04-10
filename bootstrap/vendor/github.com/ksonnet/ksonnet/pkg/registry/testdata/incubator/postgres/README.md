# postgres

> PostgreSQL is a powerful, open source object-relational database system. It has more than 15 years of active development and a proven architecture that has earned it a strong reputation for reliability, data integrity, and correctness.

* [Quickstart](#quickstart)
* [Using Prototypes](#using-prototypes)
  * [io.ksonnet.pkg.postgres-simple](#io.ksonnet.pkg.postgres-simple)

## Quickstart

*The following commands use the `io.ksonnet.pkg.postgres-simple` prototype to generate Kubernetes YAML for postgres, and then deploys it to your Kubernetes cluster.*

First, create a cluster and install the ksonnet CLI (see root-level [README.md](rootReadme)).

If you haven't yet created a [ksonnet application](linkToSomewhere), do so using `ks init <app-name>`.

Finally, in the ksonnet application directory, run the following:

```shell
# Expand prototype as a Jsonnet file, place in a file in the
# `components/` directory. (YAML and JSON are also available.)
$ ks prototype use io.ksonnet.pkg.postgres-simple postgres \
  --name postgres \
  --namespace default \
  --password boots

# Apply to server.
$ ks apply -f postgres.jsonnet
```

## Using the library

The library files for postgres define a set of relevant *parts* (_e.g._, deployments, services, secrets, and so on) that can be combined to configure postgres for a wide variety of scenarios. For example, a database like Redis may need a secret to hold the user password, or it may have no password if it's acting as a cache.

This library provides a set of pre-fabricated "flavors" (or "distributions") of postgres, each of which is configured for a different use case. These are captured as ksonnet *prototypes*, which allow users to interactively customize these distributions for their specific needs.

These prototypes, as well as how to use them, are enumerated below.

### io.ksonnet.pkg.postgres-simple

Deploy postgres backed by a persistent volume. Postgres container is managed by a deployment object and exposed to the network with a service. The
passwords are stored in a secret.

#### Example

```shell
# Expand prototype as a Jsonnet file, place in a file in the
# `components/` directory. (YAML and JSON are also available.)
$ ks prototype use io.ksonnet.pkg.postgres-simple postgres \
  --name YOUR_NAME_HERE \
  --namespace YOUR_NAMESPACE_HERE \
  --password YOUR_PASSWORD_HERE
```

Below is the Jsonnet file generated by this command.

```
// postgres.jsonnet
<JSONNET HERE>
```

#### Parameters

The available options to pass prototype are:

* `--name=<name>`: Name of app to attach as identifier to all components [string]
* `--namespace=<namespace>`: Namespace to specify destination in cluster; default is 'default' [string]
* `--password=<password>`: Password for the root/admin user. [string]


[rootReadme]: https://github.com/ksonnet/mixins