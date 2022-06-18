# Demo1 - Basic Object Detection


This is a hello world DeepStream application using Graph Composer. 
The application is a basic object detection using an mp4 file as input and RTSP as output.

The graph should simply contain the following components:
- NvDsSingleSrcInput : Parameterise video input URI
- NvDsStreamMux : make batch size = 1 and width=1920 and height=1080
- NvDsInferVideo : Select input model config to point to Resnet10 4 class
- NvDsPerClassObjectCounting
- NvsOSD
- NvDsVideoRenderer or RTSP
- NvDsScheduler

Create parameter files and set video URI to `file:///opt/nvidia/deepstream/deepstream/samples/streams/sample_1080p_h264.mp4`


Run the demo:

```bash
/opt/nvidia/graph-composer/execute_graph.sh ./demo1.yaml \
    ./demo1.parameters.yaml \
    -d /opt/nvidia/graph-composer/config/target_x86_64.yaml
```

Output can be viewed using VLC on `rtsp://<server-ip>:8554/ds-test`


