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

- SMSG_CONNECT_ACCEPTED : C2 00 00 00
int32: unknown (filled 0)  
int32: unknown (filled 0)  
int32: unknown (filled 0)
int32: ApplicationDescSize
int32: ApplicationDescFlags
int32: max player count  
int32: current player count  
byte: player name length  
bytes: unknown (always 01 00 00)  
int32: server name length  
int32: unknown (filled 0)  
int32: unknown (filled 0)  
int32: unknown (filled 0)  
int32: unknown (filled 0)  
int32: seems to be an offset related to player name length. accepted value: 204 + player name length  
int32: unknown  
uuid (16 bytes): instance guid  
uuid (16 bytes): game guid  
loop for players as player starting with current player: (to finish)  
    int32: player id  
    int32: player type?  
    int32: unknown  
    int32: unknown  
    int32: unknown  
int32: playerid  
int32: unknown  
int32(?): unknown  
int32: unknown  
int32: unknown (filled 0)  
int32: unknown  
int32: unknown (always cc)  
int32: player name length  
int32: unknown (filled 0)  
int32: unknown (filled 0)  
int32: unknown (filled 0)  
int32: unknown (filled 0)  
string: player name  
byte: map id  
byte: game type  
byte: game teams  
byte: unknown  
short: game version  
short: unknown  
short: points per capture  
short: points per kill  
short: unknown  
short: detente time in minutes  
int32: map checksum  
string: map name  
(optional): 0 padding until map name is 32 bytes long  
string: server name  
