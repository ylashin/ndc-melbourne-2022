# Demo1 - Basic Object Detection

Simplest example of using DeepStream for object detection. Demonstrates decoding video from a file, performing object detection and overlaying bounding boxes on the frames.

This is the `hello` world DeepStream application using Graph Composer. 

The graph should simply contain the following components:
- NvDsSingleSrcInput : Parameterise video input URI
- NvDsStreamMux : make batch size = 1 and width=1920 and height=1080
- NvDsInferVideo : Select input model config to point to Resnet10 4 class
- NvDsPerClassObjectCounting
- NvsOSD
- NvDsVideoRenderer or RtspOutput
- NvDsScheduler


<img width="1324" alt="image" src="https://user-images.githubusercontent.com/2197158/174426433-9cbf9e31-3a2a-49f4-b638-b20d4659fea9.png">


Create parameter file and set video URI to `file:///opt/nvidia/deepstream/deepstream/samples/streams/sample_1080p_h264.mp4`


Run the demo:

```bash
/opt/nvidia/graph-composer/execute_graph.sh ./demo1.yaml \
    ./demo1.parameters.yaml \
    -d /opt/nvidia/graph-composer/config/target_x86_64.yaml
```

Output can be viewed using VLC on `rtsp://<server-ip>:8554/ds-test`.


