
# Demo4 - Cloud to device messaging and smart record
DeepStream reference application which demonstrates device-to-cloud and cloud-to-device messaging and Smart Record.

There is an issue when running this C++ application on x86 Ubuntu 20.04.
Some time function does not work as expected an requires a slight change as below.
Update file `/opt/nvidia/deepstream/deepstream/sources/apps/apps-common/src/deepstream_c2d_msg_util.c`
 - Go to function `nvds_c2d_str_to_second`
 - Add `tm_log.tm_isdst = 0;` before line ` t1 = mktime (&tm_log);`
 - This is explained [here](https://en.cppreference.com/w/cpp/chrono/c/mktime)
   > If the std::tm object was obtained from std::get_time or the POSIX strptime, the value of tm_isdst is indeterminate, and needs to be set explicitly before calling mktime.
- Compile `/opt/nvidia/deepstream/deepstream/sources/apps/sample_apps/deepstream-test5`, instructions are in the README file in same folder.


Provide the needed Kafka connection details in `kafka-config.txt` file.


On the host machine run the below in two terminal sessions to prepare input RTSP feed:
- Start [SimpleRTSPServer](https://github.com/aler9/rtsp-simple-server)
- Run RTSP feed `ffmpeg -re -stream_loop -1 -i ./sample_1080p_h264.mp4 -c copy -f rtsp rtsp://127.0.0.1:8554/mystream`






Run the C++ app:

```bash
cd /opt/nvidia/deepstream/deepstream/sources/apps/sample_apps/deepstream-test5
./deepstream-test5-app -c configs/test5_dec_infer-resnet_tracker_sgie_tiled_display_int8.txt -m 1
```


Once the application is running you, can post a message to `commands` topic to start/stop recording as follows:

```json
{
    "command": "start-recording",
    "start": "2022-06-19T10:56:00",
    "sensor": {
        "id": "0"
    }
}
```


```json
{
    "command": "stop-recording",
    "sensor": {
        "id": "0"
    }
}
```

The `start` element could be filled as any date in the future, the program will clip it to the current time.
