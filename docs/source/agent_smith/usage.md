# Agent Smith - User Guide

The area of documentation seeks to inform the end user the basics for using Agent Smith, and is not
intended for a developer.

## Where to get the software.

Agent Smith is automatically built and packaged each time the main branch updates.  The GitHub
releases mechanism houses the executable binary.

In a browser navigate to https://github.com/agentsofthesystem/agent-smith/releases, find the most
recent release and download "agent-smith.exe" to your machine.

Verify the checksum of the "agent-smith.exe" file by comparing the computed checksum with the
value stored in checksum.exe

Easy way - Open powershell
```
Get-FileHash -Algorithm [MD5|SHA1|SHA256] <C:\Path\To\File>
```

## How to launch the software.

Once agent-smith.exe is downloaded, move the file to a location that best suits you.  The author
recommends a place that won't change and is easily accessible, like your desktop.

Onces a suitable location, to launch the software simply double-click it to run it.  You'll be prompted
that the software is a potential threat, and you'll have to click "run anyway" to make windows run
it.

After Agent Smith has launched, a green agent icon will appear in the bottom right of your screen.
Right clicking the icon reveals the menu.

### A word about Windows.

For security concerns and warnings regarding windows, please read the [Windows Security](./security.html#windows-security)
section.

All instructions were written with Windows 10 & 11 in mind,

## Files and Folders Agent Smith Creates

Agent Smith creates the following directory structure:

1. games - By default games get installed into this sub-directory. The user may optionally install
           games elsewhere.
2. nginx - All things nginx go into this folder.
3. ssl - The SSL public certificate and private key are stored in this folder.
4. steam - The SteamCMD client is kept in this folder.
5. AgentSmith.db - This is an sqlite database that keeps track of everything that Agent Smith needs.

Here is how the files look on the file system:
```
C:.
├───AgentSmith
    └───games
    └───nginx
        └───nginx-<version>
        └───nginx-<version>/nginx.exe
        └───nginx-<version>/logs
    └───ssl
    └───steam
    └───AgentSmith.db
```

### Nginx Info

As of writing, Agent Smith does not have the ability to change this location or move it.  There are
useful files in the logs folder.

There is access.log in the logs folder and it will report any and all HTTP requests that came to your
Agent Smith.

There is error.log in the logs folder and it will show any error messagse coming from nginx.exe.

There is a conf folder, if you mess with nginx.conf the app will not work.  However, feel free to
view it if interested in how nginx is configured.

### SQLite Database Info

A word about the sqlite database.  Deleting this file result in Agent Smith recieving a wipe.  You'll
be back to a fresh installation, essentially.  Only modify or edit this file if you really know
what you're doing.

## Windows Firewall

Windows Firewall will always be something to deal with.  Whenever a new game is installed and run
for the first time, windows will attempt to prompt the user to allow the app through the firewall.
However, sometimes this automation doesn't work.  Therefore, it's important to know how to
get at least nginx.exe through the firewall.

1. Open Start Menu
2. Search "Allow an App through the Windows firewall" and open.
3. Click "Change Settings"
4. If nginx.exe (or whatever app you're searching for is in the list) is present, skip on to
   step 7.
5. Click "Allow another app" and give it "C:\AgentSmith\nginx\nginx-[nginx ver]\nginx.exe"
   with the browse button.
6. Click Add
7. Check the box for both public and private.
8. Click OK to finish.

## Instructions to install a game server

To install a supported game:

1. Right click Agent Smith's icon in the system application tray.
2. Select New Game.
3. Chose the game server you wish to install in the dropdown.
4. There will be defaults, but alter any of the installation settings as desired.
5. Click the installation button at the bottom.

## Instruction to start stop an installation.

There are two methods to quickly startup a server and shut one down.

### Using the Game Manager windows:

1. Right click Agent Smith's icon in the system application tray.
2. Select New Game.
3. Chose the game server you wish to manage in the dropdown.
4. On the bottom you can click one of Startup/Shutdown/Restart as needed.

### Using the Quick Action Menu:

Agent Smith allows the user to quickly startup or shutdown a server without going through the Game
Manager windows.

1. Right click Agent Smith's icon in the system application tray.
2. Hover your cursor over "Quck Action"
3. Click the game server you want to toggle.  If the game server is red, that means its off and clicking
   it will initiate startup.  Conversley if the game server is green, clicking it will shutdown the
   game server.

## Instructions to modify a game server's inputs.

The definition of an argument in the context of a game server is a mechanism to give the user control
over either the configuration of the server and/or the game settings itself.

Agent Smith attempts to generalize some game servers ability to change things like a server port via
an Arguments Mechanism.  No two game servers are different.

There are roughtly a few categories:

1. Servers that take no argument(s) and instead rely on a file being in a specific location.
2. Servers that take only or a combination of input arguments.
3. Servers have arguments that point to a specific configuration file.

Each game is tailored to whatever method the game developers chose to feed user input into their dedicated
game server.  However, not everything is exposed or perfectly provided via GUI.

Examples:
* Vrising - The user game modify a subset of server settings via GUI but not global game settings.
  Instead, the user would need to modify the files on the file system after installation.
* 7DTD - This game server simply points to a file on the file system that the user can manipulate
  after installation.

To modify server arguments expose via GUI that's done either at installation time, or via the
Game Manager window when the server is shutdown.

WARNING:
* Some games servers, like PalWorld for example, require Agent Smith to use a file template that is
  overwritten each time the server is started.  So only through software modification can additional
  inputs be exposed.

## Reporting Bugs

Things happen, don't work as expected, and many many more issues.  If it happens to you, then fill
out the bug template in GitHub [here](https://github.com/agentsofthesystem/agent-smith/issues/new?assignees=&labels=bug&projects=&template=bug_report.md&title=%5BBUG%5D+%5BGUI%2C+Backend%2C+Client%5D+-+Short+Subject).

Please don't confuse feature requests with a bug... Thanks in advance!  Ask questions!
