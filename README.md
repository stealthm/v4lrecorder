# v4lrecorder
This is a simple script to record video with audio from a v4l2 device (web camera) like a DVR

The video is recorded in 10-minute chunks of the /YYYY/MM/DD/HHM0-DDMM.mp4 format

## Dependencies

alsa-utils
v4l-utils
ffmpeg

## Usage

**v4lrecorder** - script to record video with audio in 1-minute chunks

1. Identify video and audio devices:
v4l2-ctl --list-devices

arecord -L

3. Select the maximum resolution and frame rate:
v4l2-ctl -d /dev/video0 --list-formats-ex

4. Edit the variables in the script

5. Run the script through the service v4lrecorder.service

**mergerecords** - a script for combining files into 10-minute parts and archiving by directories

1. Edit the variables in the script

2. Run it through the crontab
2,12,22,32,42,52 * * * * root /opt/v4lrecorder/mergerecords >>/var/log/recorder/
merge.log 2>&1

Tested on Ubuntu 24 with Creative Live! Cam Sync 4K

