# Demo5 - Analytics : Line crossing and region of interest

This application shows how to count objects crossing a line or found in a certain region of interest.

Run the below snippet (make sure demo 4 is stopped as it would be locking RTSP port):

```bash
/opt/nvidia/graph-composer/execute_graph.sh \
    ./demo5.yaml \
    -d /opt/nvidia/graph-composer/config/target_x86_64.yaml
```

Output can be viewed using VLC on `rtsp://<server-ip>:8554/ds-test`.


