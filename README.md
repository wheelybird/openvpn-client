### An OpenVPN client


This is a very basic OpenVPN client container designed to be used on the host network.

You'll need to bind mount a directory containing your configuration files into the container and set `CLIENT_FILE` accordingly.

This container requires the *NET_ADMIN* capability in order to create the tunnel and add various routes:  `--cap-add=NET_ADMIN`.   


#### Running the container

```
docker run \
            --detach=true \
            --restart=unless-stopped \
            --network=host \
            --name=openvpn_client \
            --volume=/opt/docker/openvpn_client:/opt/config \
            -e "CLIENT_FILE=/opt/config/client.ovpn" \
            --cap-add=NET_ADMIN \
            wheelybird/openvpn-client
```

#### Environmental variables

`CLIENT_FILE`: The location (in the container) of the OpenVPN client configuration file.

