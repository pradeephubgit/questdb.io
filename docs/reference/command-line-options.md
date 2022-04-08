---
title: Command-line options
description: Command-line options reference documentation.
---

From the command-line interface (CLI), you can start, stop, and pass configuration options to QuestDB. On Windows, you can also use the QuestDB server to start an [interactive session](#interactive-session-windows).

## Options

From the CLI, you can use the following options to configure the QuestDB server:

<!-- prettier-ignore-start -->

import Tabs from "@theme/Tabs"
import TabItem from "@theme/TabItem"

<Tabs defaultValue="nix" 
values={[ 
  { label: "Linux/FreeBSD", value: "nix" }, 
  { label: "macOS (Homebrew)", value: "macos" }, 
  { label: "Windows", value: "windows" },
]}>

<!-- prettier-ignore-end -->

<TabItem value="nix">


```shell
./questdb.sh [start|stop|status] [-d dir] [-f] [-t tag]
```

</TabItem>


<TabItem value="macos">


```shell
questdb [start|stop|status] [-d dir] [-f] [-t tag]
```

</TabItem>


<TabItem value="windows">


```shell
questdb.exe [start|stop|status|install|remove] \
  [-d dir] [-f] [-j JAVA_HOME] [-t tag]
```

</TabItem>


</Tabs>


### Start

`start` - starts QuestDB as a service.

| Option | Description                                                                                                                                                                                                          |
| ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-d`   | `dir` directory value. This folder is used as QuestDB's root directory. For more information and the default values, see [default root](#default-root-directory).         |
| `-t`   | `tag` string value for the service. If you specify a tag, it enables you to run several QuestDB services and manage them separately. If you omit this option, `questdb` is enabled as the default tag value. |
| `-f`   | Force re-deploying the Web Console. Without this option, the Web Console is cached and deployed only when missing.                                                                                                   |
| `-j`   | **Windows only!** If you enable this option, you can specify a path to `JAVA_HOME`.                                                                                                                                               |

:::info

When you run multiple QuestDB services, use a tag for each service. If only
one tag is specified for multiple services, it leads to port and root directory
conflicts, especially with `start` and `stop` commands. Start each new service
with a separate port and root directory, or create a unique config file for the service.

:::

<!-- prettier-ignore-start -->


<Tabs defaultValue="nix" 
values={[ 
  { label: "Linux/FreeBSD", value: "nix" }, 
  { label: "macOS (Homebrew)", value: "macos" }, 
  { label: "Windows", value: "windows" },
]}>

<!-- prettier-ignore-end -->

<TabItem value="nix">


```shell
./questdb.sh start [-d dir] [-f] [-t tag]
```

</TabItem>


<TabItem value="macos">


```shell
questdb start [-d dir] [-f] [-t tag]
```

</TabItem>


<TabItem value="windows">


```shell
questdb.exe start [-d dir] [-f] [-j JAVA_HOME] [-t tag]
```

</TabItem>


</Tabs>


#### Default root directory

QuestDB's default [root directory](/docs/concept/root-directory-structure/):

<!-- prettier-ignore-start -->

<Tabs defaultValue="nix" values={[
  { label: "Linux/FreeBSD", value: "nix" },
  { label: "macOS (Homebrew)", value: "macos" },
  { label: "Windows", value: "windows" },
]}>

<!-- prettier-ignore-end -->

<TabItem value="nix">


```shell
$HOME/.questdb
```

</TabItem>


<TabItem value="macos">


```shell
/usr/local/var/questdb
```

</TabItem>


<TabItem value="windows">


```shell
C:\Windows\System32\questdb
```

</TabItem>


</Tabs>


### Stop

`stop` - stops a service.

| Option | Description                                                                                                        |
| ------ | ------------------------------------------------------------------------------------------------------------------ |
| `-t`   | `tag` string value to stop a service. If you omit this option, `questdb` is enabled as the default tag value.|

<!-- prettier-ignore-start -->

<Tabs defaultValue="nix" values={[
  { label: "Linux/FreeBSD", value: "nix" },
  { label: "macOS (Homebrew)", value: "macos" },
  { label: "Windows", value: "windows" },
]}>

<!-- prettier-ignore-end -->

<TabItem value="nix">


```shell
./questdb.sh stop
```

</TabItem>


<TabItem value="macos">


```shell
questdb stop
```

</TabItem>


<TabItem value="windows">


```shell
questdb.exe stop
```

</TabItem>


</Tabs>


### Status

`status` - shows the status of a service.

<!-- prettier-ignore-start -->

<Tabs defaultValue="nix" values={[
  { label: "Linux/FreeBSD", value: "nix" },
  { label: "macOS (Homebrew)", value: "macos" },
  { label: "Windows", value: "windows" },
]}>

<!-- prettier-ignore-end -->

<TabItem value="nix">


```shell
./questdb.sh status
```

</TabItem>


<TabItem value="macos">


```shell
questdb status
```

</TabItem>


<TabItem value="windows">


```shell
questdb.exe status
```

</TabItem>


</Tabs>


### Install (Windows)

`install` - installs the Windows QuestDB service. The service starts automatically at startup.

```shell
questdb.exe install
```

### Remove (Windows)

`remove` - removes the Windows QuestDB service. It will no longer start at
startup.

```shell
questdb.exe remove
```

## Interactive session (Windows)

You can start QuestDB interactively by running `questdb.exe`. This will launch
QuestDB interactively in the active `Shell` window. QuestDB is stopped when
the Shell is closed.

### Default root directory

When started interactively, QuestDB's root directory defaults to the `current`
directory.

### Stop

To stop, press <kbd>Ctrl</kbd>+<kbd>C</kbd> in the terminal or close it
directly.
