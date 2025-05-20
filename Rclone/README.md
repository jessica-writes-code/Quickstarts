# Rclone

This is a "Quickstart" guide for simple Rclone usage.

## What is Rclone?

[RClone](https://rclone.org)

Rclone is a command-line program designed to manage files in cloud storage. It serves as an alternative to the interfaces provided by cloud vendors. Rclone supports over 70 different cloud storage products including S3 object stores and various file storage services. Rclone offers equivalents to many Unix commands such as rsync, cp, mv, etc. It ensures data integrity by preserving timestamps and verifying checksums, and it can handle transfers over limited bandwidth or intermittent connections.

## Quickstart Guide: rclone copy

These instructions assume that you are using a Linux-based operating system.

1. Set up Rclone on your machine.

```
sudo apt-get update
sudo curl https://rclone.org/install.sh | sudo bash
```

2. Use `rclone config` to set up source and destination remotes. Follow on-screen prompts to configure each appropriately.

In Rclone, a "remote" refers to a specific cloud storage service. Remotes are used to specify the source and destination locations for file operations such as copying, syncing, and moving files. Each remote is identified by a unique name and contains the necessary credentials and settings to access the corresponding storage service.

3. Use `rclone copy` to copy files from one location to another.

```
rclone copy sourceRemote:path/to/files destinationRemote:path/to/destination --progress --tpslimit 5 --include=*.{pdf,mp4}
```

In this example, sourceRemote and destinationRemote are the names of the configured remotes, and path/to/files and path/to/destination are the paths within those remotes, e.g., folder structure within the remote.

The following options are also useful, but may be ignored if you prefer.
* `--progress`: This option displays a progress bar during the file transfer, showing the current status of the operation.
* `--tpslimit`: This option limits the number of transactions per second (TPS) to the specified value. It is useful for controlling the rate of API requests to avoid hitting rate limits imposed by cloud storage providers.
* `--include=*.{pdf,mp4}`: This option allows you to include only files that match the specified pattern(s) in the operation. For example, --include=*.{pdf,mp4} includes only files with .pdf or .mp4 extensions in the operation.
