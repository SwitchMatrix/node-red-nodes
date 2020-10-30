node-red-contrib-sshtools
=======================

A <a href="http://nodered.org" target="_new">Node-RED</a> set of nodes that will connect to SSH server
and provide TCP like communication node and other utility operations.

Install
-------

Run the following command in your Node-RED user directory - typically `~/.node-red`

        npm install node-red-contrib-sshtools

Usage
-----

### sshtun_in

A SSH Tunnel in node provides a choice of inputs. Can either connect to a remote
TCP port, or accept incoming connections.

**NOTE:** On some systems you may need root or administrator access to ports below 
1024. Also some SSH servers will only allow binding reverse tunnels to localhost
interfaces.

### sshtun_out

A SSH Tunnel out node provides a choice of outputs. Can either connect to a remote
TCP port, or accept incoming connections.

Only the `msg.payload` is sent.

If `msg.payload` is a string containing Base64 encoding of binary data,
the Base64 decoding option will cause it to be converted back to binary before being
sent.

If `msg._session` is not present the payload is sent to **all**
connected streams under the control of the `SSHTun Credential` node

**Note:** On some systems you may need root or administrator access to ports below 
1024. Also some SSH servers will only allow binding reverse tunnels to localhost 
interfaces.

### sshtun_req

A SSH Tunnel request node - sends the `msg.payload` to a server tcp port and expects a 
response.

`msg.payload` the data sent as part of the request.

`msg.host` the hostname or IP address of the remote host to send the request.

`msg.port` the port of the remote host to send the request.

**Details**
Connects, sends the "request", and reads the "response". It can either
count a number of returned characters into a fixed buffer, match a specified
character before returning, wait a fixed timeout from first reply and then
return, sit and wait for data, or send then close the connection immediately,
without waiting for a reply.

The response will be output in `msg.payload` as a buffer, so you may want 
to .toString() it.

If you leave remote host or port blank they must be set by using the
`msg.host` and `msg.port` properties in every message sent to the node.
