# Master Server

The Giants master handles the listing of active Giant game servers and listens on TCP port 27900.

## Response

The master server will output the following response as a null terminated string in ASCII format:

```00¬192.168.1.100¬19711¬01¬192.168.1.101¬19700\0```

The following response will list two servers:

- `192.168.1.100` listening on port `19711`
- `192.168.1.101` listening on port `19710`

