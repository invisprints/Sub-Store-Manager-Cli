# Sub-Store-Manager-Cli

English | [简体中文](./README-CN.md)

A CLI tool for managing [Sub-Store](https://github.com/sub-store-org/Sub-Store) backend service. Because of this tool based on [docker](https://www.docker.com/), you should install docker first.


# Install

You can install this tool by running the following command:

```bash
curl -sSL https://desnlee.github.io/Sub-Store-Manager-Cli/install.sh | bash
```

Or you can download [release binary](https://github.com/DesnLee/Sub-Store-Manager-Cli/releases) and configure your environment variable manually.


# Usage

If you are using a script installation, you can directly execute the following commands. However, if you are doing a manual installation, please make sure to modify the program name in each command to match the executable file name.


### new

Create a new sub-store docker container and run it. If the Image does not exist, it will be build automatically.

```bash
ssm new
```

this command support the following flags:

- `--name` or `-n` : A unique name for the container, default name is `sub-store-manager-backend`. This name will be used to manage persistent data. As long as the persistent data with this name is not manually deleted, or execute `ssm delete` with `-c` flag, it will be accessible whenever the container is rebuilt or when the image is deleted and then launched using this name.

- `--version` or `-v` : A [Sub-Store release](https://github.com/sub-store-org/Sub-Store/releases) version string, default is latest.

- `--port` or `-p` : To successfully create a new Docker container, you need to specify the port mapping. The default port is `3000`, and it must be available. If you want to access the container using a domain name, you will need to manually proxy this port with a reverse proxy tool such as Nginx or Caddy.


### start

Start a non-running sub-store Docker container by name, default name set as `sub-store-manager-backend`.

> Equivalent to `docker start <name>`.

```bash
ssm new <name>
```


### stop

Stop a running sub-store Docker container by name, default name set as `sub-store-manager-backend`.

> Equivalent to `docker stop <name>`.

```bash
ssm stop <name>
```


### delete

Delete a sub-store Docker container by name, default name set as `sub-store-manager-backend`.

> Equivalent to `docker rm -f <name>`.

```bash
ssm delete <name>
```

this command support the following flags:

- `--clear` or `-c` : Delete the persistent data of the container at the same time.


### update

Update a sub-store Docker container by name, default name set as `sub-store-manager-backend`.

```bash
ssm update <name>
```

this command support the following flags:

- `--version` or `-v` : A [Sub-Store release](https://github.com/sub-store-org/Sub-Store/releases) version string, default is latest. You can use this flag to downgrade the version of the container.


### list

List all sub-store Docker containers.

> Equivalent to `docker ps -a`, filter images with names starting with `sub-store-manager-backend`.

```bash
ssm ls
```


### version

Print the version number of ssm.

```bash
ssm version
```


# Uninstall

If you are using a script installation, you can directly execute the following command. If you are doing a manual installation, please manually remove your executable file.

```bash
rm -rf /usr/local/bin/ssm
```

If you want to delete the persistent data of the container at the same time, you can execute the following command:

```bash
rm -rf ~/.ssm
```


# License
GPL-2.0 License