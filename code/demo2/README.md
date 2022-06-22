# Demo2 - Object Tracking and cascaded inference

This application is a Graph Composer reference app showing object trancking and cascaded inference.
It builds on top of demo1 and adds plugins for object tracking and secondary ML inference.

<img width="1317" alt="image" src="https://user-images.githubusercontent.com/2197158/174428626-cb2adc62-05ab-4aca-9dd5-92605313a828.png">


Run the demo:

```bash
/opt/nvidia/graph-composer/execute_graph.sh ./demo2.yaml \
    -d /opt/nvidia/graph-composer/config/target_x86_64.yaml
```

Output can be viewed using VLC on `rtsp://<server-ip>:8554/ds-test`.


