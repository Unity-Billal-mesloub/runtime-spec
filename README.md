# Open Container Initiative Runtime Specification

[![GitHub Actions status](https://github.com/Unity-Billal-mesloub/runtime-spec/workflows/build/badge.svg)](https://github.com/Unity-Billal-mesloub/runtime-spec/actions?query=workflow%3Abuild)

The [Open Container Initiative][oci] develops specifications for standards on Operating System process and application containers.

The specification can be found [here](spec.md).

## Table of Contents

Additional documentation about how this group operates:

- [Code of Conduct][code-of-conduct]
- [Style and Conventions](style.md)
- [Implementations](implementations.md)
- [Releases](RELEASES.md)
- [charter][charter]

## Use Cases

To provide context for users the following section gives example use cases for each part of the spec.

### Application Bundle Builders

Application bundle builders can create a [bundle](bundle.md) directory that includes all of the files required for launching an application as a container.
The bundle contains an OCI [configuration file](config.md) where the builder can specify host-independent details such as [which executable to launch](config.md#process) and host-specific settings such as [mount](config.md#mounts) locations, [hook](config.md#posix-platform-hooks) paths, Linux [namespaces](config-linux.md#namespaces) and [cgroups](config-linux.md#control-groups).
Because the configuration includes host-specific settings, application bundle directories copied between two hosts may require configuration adjustments.

### Hook Developers

[Hook](config.md#posix-platform-hooks) developers can extend the functionality of an OCI-compliant runtime by hooking into a container's lifecycle with an external application.
Example use cases include sophisticated network configuration, volume garbage collection, etc.

### Runtime Developers

Runtime developers can build runtime implementations that run OCI-compliant bundles and container configuration, containing low-level OS and host-specific details, on a particular platform.

### Discuss your design

The project welcomes submissions, but please let everyone know what you are working on.

Before undertaking a nontrivial change to this specification, send mail to the [mailing list](#mailing-list) to discuss what you plan to do.
This gives everyone a chance to validate the design, helps prevent duplication of effort, and ensures that the idea fits.
It also guarantees that the design is sound before code is written; a GitHub pull-request is not the place for high-level discussions.

Typos and grammatical errors can go straight to a pull-request.
When in doubt, start on the [mailing-list](#mailing-list).

### Mailing List

You can subscribe and join the mailing list on [Google Groups][dev-list].

### Chat

OCI discussion happens in the following chat rooms, which are all bridged together:

- #general channel on [OCI Slack](https://opencontainers.org/community/overview/#chat)
- #opencontainers:matrix.org

### Git commit

#### Sign your work

The sign-off is a simple line at the end of the explanation for the patch, which certifies that you wrote it or otherwise have the right to pass it on as an open-source patch.
The rules are pretty simple: if you can certify the below (from https://developercertificate.org):

```
Developer Certificate of Origin
Version 1.1

Copyright (C) 2004, 2006 The Linux Foundation and its contributors.
660 York Street, Suite 102,
San Francisco, CA 94110 USA

Everyone is permitted to copy and distribute verbatim copies of this
license document, but changing it is not allowed.


Developer's Certificate of Origin 1.1

By making a contribution to this project, I certify that:

(a) The contribution was created in whole or in part by me and I
    have the right to submit it under the open source license
    indicated in the file; or

(b) The contribution is based upon previous work that, to the best
    of my knowledge, is covered under an appropriate open source
    license and I have the right under that license to submit that
    work with modifications, whether created in whole or in part
    by me, under the same open source license (unless I am
    permitted to submit under a different license), as indicated
    in the file; or

(c) The contribution was provided directly to me by some other
    person who certified (a), (b) or (c) and I have not modified
    it.

(d) I understand and agree that this project and the contribution
    are public and that a record of the contribution (including all
    personal information I submit with it, including my sign-off) is
    maintained indefinitely and may be redistributed consistent with
    this project or the open source license(s) involved.
```

then you just add a line to every git commit message:

    Signed-off-by: Joe Smith <joe@gmail.com>

using your real name (sorry, no pseudonyms or anonymous contributions.)

You can add the sign off when creating the git commit via `git commit -s`.

#### Commit Style

Simple house-keeping for clean git history.
Read more on [How to Write a Git Commit Message][how-to-git-commit] or the Discussion section of [git-commit(1)][git-commit.1].

1. Separate the subject from body with a blank line
2. Limit the subject line to 50 characters
3. Capitalize the subject line
4. Do not end the subject line with a period
5. Use the imperative mood in the subject line
6. Wrap the body at 72 characters
7. Use the body to explain what and why vs. how
    * If there was important/useful/essential conversation or information, copy or include a reference
8. When possible, one keyword to scope the change in the subject (i.e. "README: ...", "runtime: ...")


