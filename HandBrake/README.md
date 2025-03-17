# HandBrake

This is a "Quickstart" guide for simple HandBrake usage.

## What is HandBrake?

[HandBrake](https://handbrake.fr)

HandBrake is an open-source video transcoder that allows you to convert video files from nearly any format to a selection of modern, widely supported codecs. It is available for Windows, Mac, and Linux, and it provides a range of features including batch processing, chapter markers, and subtitle support.

## Quickstart Guide: Changing video quality with HandBrake


1. Install HandBrake:

    ```sh
    sudo apt-get update
    sudo apt install -y flatpak handbrake-cli
    ```

2. Use HandBrake CLI to change the quality of a video:

    ```sh
    HandBrakeCLI -i /path/to/input/file.mp4 -o /path/to/output/file.mp4 -q 30 < /dev/null
    ```

Here, the number specified after `-q` is the quality level, with lower numbers indicating higher quality.
