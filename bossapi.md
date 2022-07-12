## AGNET Boss API

The AGNET Boss API is a group of function packed files that automate the AGNET process. 

### What is AGNET Boss API coded in?

AGNET Boss API is primarly coded in **Lua**.

### Index
- **[Back To Homepage]**(https://agprograms.github.io/)
- [Auth API](#auth-api)
- [Deploy AGNET](#deploy-agnet-boss-and-webservices)

### Auth API
```lua
require(/settings.lua) -- get srvSel global
agProtocol = 'AUTH-AGNET'
agLocal = tostring(os.getcomputerID())
local event, sender, message, protocol = os.pullEvent("rednet_message")
rednet.send(srvSel, agLocal, agProtocol)
```
The **agProtocol** is a defined *global string* to be used in the ```lua  rednet.send(args)``` command, under protocol. When sending a message with this protocol, the Boss Server will filter and engage the proper **LOGINREQ.SYS** function in the API. Within this function, the Boss Server will check for the **sender**'s file within its local file system. Formatted as /usrs/**sender**.usr. If the user exists, it will return the sender's **screenname**. If the **screenname** matches the screenname stored on the client's machine's *settings.lua* then the Boss Server will pass **LOGIN.SUCCESS** via a string in ```lua rednet.send(sender,'LOGIN.SUCCESS',agProtocol)```. To which the client begins to actively receive and look for that message after it receives the **LOGIN.SYS** response.
