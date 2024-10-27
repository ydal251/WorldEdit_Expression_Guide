# Appendix C \- Running Very Long Expressions {#appendix-c---running-very-long-expressions}

You may come across a situation where you want to bypass the 256 character limit inherent with using commands via Minecraft’s chat.  
There are two main ways to achieve this, Command Blocks and Scripts.

## **Scripts** {#scripts}

Without going too much into scripts at this time, there are several different plugins that allow you to bypass the chat limit by running your intended command via a script instead. One example is [CommandHelper](https://www.spigotmc.org/resources/commandhelper.64681/) which allows you to setup a command alias.

You may want to run a //generate command which is \>256 characters long, and you could put that into the CommandHelper scripts and call it with some alias command like */longcommand*.

## **Command Blocks** {#command-blocks}

Command Blocks are the more likely method you would want to use as they are built into the game. However, you will need Operator access on the server so unless it is your own server or one where you are an administrator, this is going to be a limiting factor to most.

Command Blocks will run commands as the console (the server itself), so with FAWE you will need to define the world using the //world command with a command block, then set a selection with //pos1 & //pos2 for example. With standard WorldEdit you won’t need to do this.

If you want to avoid having to setup the world and selection, then using the functionality of another plugin to allow the command block to run commands as a player can be helpful. The [Essentials plugin](https://essentialsx.net/) has the command /sudo which you can use in the command block to use your own selections, masks, etc.[^17]

[^17]: There is a potential 2,000 character limitation on WE commands in a commandblock