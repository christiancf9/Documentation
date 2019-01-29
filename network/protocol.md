# Giants Network Protocol

The Giants network protocol runs on the Direct Play 8 protocol created by Microsoft.

## Direct Play 8 Documentation

The Direct Play 8 protocol is well-documented and can be found on the MSDN website.

The protocol consists out of multiple protocols combined together a list below:

- [[MC-DPL8R]: DirectPlay 8 Protocol: Reliable](https://msdn.microsoft.com/en-us/library/cc217167.aspx)
- [[MC-DPLHP]: DirectPlay 8 Protocol: Host and Port Enumeration](https://msdn.microsoft.com/en-us/library/cc217240.aspx)
- [[MC-DPL8CS]: DirectPlay 8 Protocol: Core and Service Providers](https://msdn.microsoft.com/en-us/library/cc217035.aspx) 

## Connection Flow

Client -> CFRAME CONNECT
Server -> CFRAME CONNECTED
Client -> CFRAME CONNECTED
Client -> CMSG_CONNECT
Server -> SMSG_CONNECT_ACCEPTED
Client -> CMSG_CONNECTED
Server -> SMSG_BLUE_MESSAGE (player has connected)
Server -> SMSG_ASSIGN_PLAYERID
...


## Application Protocol

This is still in heavy research and will be updated in the future

- SMSG_PLAYERNAMES (playerindex, playername) : 3D

Example: `3D 00 Amazed`


- CMSG_CHAT_ALL (message): 35 82 C2

Example: `85 82 C2 Hello world`


- SMSG_BLUE_MESSAGE (message): 35 80 81

Example: `35 80 81 Amazed has connected!`

- CMSG_CONNECT : C1 00 00 00
int32: unknown
int32: unknown
int32: unknown
int32: player name length
int32: unknown (filled 0)
int32: unknown (filled 0)
int32: unknown (filled 0)
int32: unknown (filled 0)
int32: unknown (filled 0)
int32: unknown (filled 0)
int32: unknown (filled 0)
int32: unknown (filled 0)
uuid (16 bytes): instance guid
uuid (16 bytes): game guid
int32: unknown (filled 0)
int32: unknown (filled 0)
variable: player name
