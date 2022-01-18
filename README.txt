This contains binaries for both Windows and Linux for the monitoring program.
It also contains a Windows ONLY build of the 2.05 DynMiner2.exe and dyn_miner2.cl for use with this monitor
Hopefully the changes needed for the miner are integrated into the Foundation build for the miner soon...

Windows:
dmo-monitor.exe

Linux: 
dmo-monitor


Usage:

This utility is designed to be used to display the realtime mining status of DynMiner2.exe miners
as well as DMO coin mining statistics for specific DMO Wallets linked to a running DMO full node.

In order to use it, you will need to do 2 things:
1) Setup the config.yaml configuration file that comes with dmo-monitor with information about your fullnode and the wallets you 
want to display statistics for.
2) When you run your DynMiner2.exe program you will just need to pass 2 additional command line options in order to connect 
to the dmo-monitor: The URL for your monitoring program and a 'vanity name' to display in the monitor, eg these are the two additional parameters to add to your DynMiner2.exe line:
-statrpcurl http://123.456.789.111:11235/minerstats -minername TestMiner

So the full line would look like:
DynMiner2.exe -mode solo -server http://192.168.1.169:6433 -user username -pass password -wallet dy1qvesdfsdfsdfsdfsdfsdfefczsvf -miner GPU,16384,8,0,0 -statrpcurl http://192.168.1.133:11235/minerstats -minername TestMiner

The -statrpcurl argument should use the IP address of the machine the dmo-monitor is running on and the port configured for that dmo-monitor in config.yaml. The '/minerstats' part should be left as-is

3) Open the configured ServerPort on the host machines firewall that is running the monitor (in the example above 11235)
4) Run the dmo-monitor executable

Once you run the executable it will immediately start to display statistics in the console. Text is formatted and colored using ANSI escape codes, so if your terminal does not support those formatting will be a little wonky, but that's fine because the web interface is much nicer looking anyhow.

This has been tested with powershell, git bash and cmd on Windows.

You can also access a webview that is mobile friendly by visiting your server IP address/port like:

localhost:11235 (11235 is the default port setup in the included config, but you can change it to whatever you like)
You can also access this view from other computers or phones by using the IP address for the computer it is running, or by forwarding out the configured port on your router firewall and the IP address assigned by your ISP.


IMPORTANT NOTE on Wallet Statistics:
If you want to display statistics on your mining wallets, the WalletsToMonitor will need to be Wallet Names that are setup on 
the full node you are mining against. There is no support for pool mining for these statistics yet.
IF all you want is to see your running miners and their hashrates, submits, rejects and accepts, 
then the ONLY option you need to set is the ServerPort (which can be left as default). You should also remove/leave the WalletsToMonitor config option BLANK in that case like:
WalletsToMonitor: 


NOTE: SMS is not yet actually supported!

