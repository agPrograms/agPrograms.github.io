## Welcome to AGNET Docs

This is a basic documentation page to learn more about AGNET and for my own personal documentation of the API as it is created.

### What is AGNET?

AGNET is a foundation for the internet, in minecraft. Combined with the desktop client, webservers, and BOSS server -- it allows users to create whatever they wish!

### What is AGNET coded in?

AGNET is primarly coded in **Lua**.

### Index
- [Download & Use AGNET](#download-and-use-agnet)
- [Deploy AGNET](#deploy-agnet-boss-and-webservices)
- [BOSS API](https://agprograms.github.com/bossapi.md/)
- [Auth API](#auth-api)

### Download and Use AGNET
Here are the current resources for AGNET:
- **AGNET Desktop**: pastebin coming soon! **Github Repo**: github coming soon!
- **AGNET Boss Server**: pastebin coming soon! **Github Repo**: github coming soon!
- **AGNET Webservices**: pastebin coming soon! **Github Repo**: github coming soon!

### Deploy AGNET BOSS and Webservices
In order for the AGNET Network/Internet Service to work, the the AGNET Boss Server is required to be set up FIRST. The AGNET Boss stores user information and data about the network. ***Note: AGNET BOSS Server does NOT record passwords natively. The BOSS Server records the Computer ID the desktop/client user is currently registering with.***

If you have not already, download the AGNET BOSS Server script/client [here](#download-and-use-agnet)

Next, follow the setup on screen. The setup is easy and guides you through the whole process. The Boss server will advertise by brodcasting with the specific AGNET protocol, and will indicate it is ready to accept client connections. **The same for webservices**.

[Back to Index](#index)

### Auth API
```lua
require(/settings.lua) -- get srvSel global
agProtocol = 'AUTH-AGNET'
agLocal = tostring(os.getcomputerID())
local event, sender, message, protocol = os.pullEvent("rednet_message")
rednet.send(srvSel, agLocal, agProtocol)
```
The **agProtocol** is a defined *global string* to be used in the ```lua  rednet.send(args)``` command, under protocol. When sending a message with this protocol, the Boss Server will filter and engage the proper **LOGINREQ.SYS** function in the API. Within this function, the Boss Server will check for the **sender**'s file within its local file system. Formatted as /usrs/**sender**.usr. If the user exists, it will return the sender's **screenname**. If the **screenname** matches the screenname stored on the client's machine's *settings.lua* then the Boss Server will pass **LOGIN.SUCCESS** via a string in ```lua rednet.send(sender,'LOGIN.SUCCESS',agProtocol)```. To which the client begins to actively receive and look for that message after it receives the **LOGIN.SYS** response.

[Back to Index](#index)

## More to come!
