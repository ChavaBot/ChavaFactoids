#### ChavaFactoids 

The general command structure will be similar to skybots so that it can be easy for anyone to use

Prefix - Command Prefixes
	? - Will be for local factoids, if no local is found it will check for a global factoid
	! - Will be for global factoids
	(!/?)+ -  Will show the raw of the factoid
	(!/?)- - Will show who set the factoid
	
Handlers - Will decide the way that the factoid is processed
	Handlers can be run recursively by using runAgain(boolean) so that a complex Handler can let simple handlers 
	Default Handlers - (Plugins can add Handlers):
		<reply> - simple reply factoid
		<action> - simple action factoid
		<notice> - simple notice factoid
		<alias> - links factoids together 
		<forget> - Forgets the factoid (cannot be applied using .r or .no, you must use .f)
		<locked> - Locks that factoid so that it cannot be changed (recursive) (cannot be applied using .r or .no, you must use .lock)
	Example of Handlers that can be added by another plugin
		<python> - Uses Jython to run the python code

Registry 
	Plugins can register Commands to factoids so that they can link similar factoids to their commands
		
Commands - 
	.r factoid [local/global(default)] <reply(default)/action/notice/alias/other> factoids params
		remembers a factoid, if one exists already it will not change
	.no factoid [local/global(default)] <reply(default)/action/notice/alias/other> factoids params
		Changes an existing factoid, if the factoid does not exist already, it will not be added
	.f factoid 
		forgets a factoid
	.lock factoid 
		Locks a factoid so that it cannot be changed
		
Flat File Structure
	/global
		/factoids.settings - holds the factoids and their value
		/info.settings - holds who set the factoid
		/lock.settings - holds who locked the factoid
		
	/local
		/channel_name - 
			/factoids.settings - holds the factoids and their value
			/info.settings - holds who set the factoid
			/lock.settings - holds who locked the factoid
			
		
SQL Support will come at a later date