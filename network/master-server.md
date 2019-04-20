# Master Server

The Giants master handles the listing of active Giant game servers and listens on TCP port 27900.

## Flow

 1. The game clients connect to the master server.
 2. The server will sent the response below to the client.
 3. The connection between the server and client will remain open as long as the client is in the server browser.

## Response

The master server will output the following response as a null terminated string in ASCII format:

```00¬192.168.1.100¬19711¬01¬192.168.1.101¬19700\0```

The following response will list two servers:

- `192.168.1.100` listening on port `19711`
- `192.168.1.101` listening on port `19710`

