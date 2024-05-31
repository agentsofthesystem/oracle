# How to use Agents

This section assumes that the reader has added at least one agent to the system for use.

* Open a browser and navigate to the [Agents](https://agentsofthesystem.com/app/system/agents) page.

There will be a list of agents.  From here, the user may do perform some functions:

1. Update the agent information, such as changing the hostname.
2. Share the agent with a group or friend(s) directly.
3. Delete the agent.

The user will see two types of agents on the list;  Agents which are owned which have a black icon, and
green agents which are shared to the user by another user.

## How sharing works with Agents.

The owner has the ability to share agents with groups and/or friends, and that
comes with some considerations.  Only the agent owner may manage the agent.

### Groups vs Friends.

The agent owner may share a group with some users already in it, share an empty
group and later add user to said group, or share with individual friends directly.

Sharing directly to friends trumps sharing to a group.  In the instance where an agent
is shared to a group with a friend inside it that also has direct shared access, then unsharing
the group will not result in eliminating access for that friend.  The agent owner would have
to also remove the direct friend access.   This is most useful when you have a permanent friend
in mind and groups and/or group members change often.

### Counting Users

Agent sharing counts the unique users between Groups and Friends.  Not
including the agent owner.

Example, let's say Agent X has been shared with Group A.  This Group A
has Friend 1 and Friend 2 inside it.  Group A also has the group owner
inside of it, and the group has a total of 3 members.   However, the share
count is 2 because sharing doesn't count the agent owner.

Let's say also, in addition to the group, the agent is shared directly with Friend 2.
The share count remains at 2 because the unique non-owner user count remains to.

Next, you share directly with Friend 3 that is not in Group A.  The share count goes
up to 3 because this is a third unique user.

## The Agent Information Page

The agent information page is the primary controls location for managing agents.  There are several sections:

1. Agent Details - Name, hostname, etc..
2. Platform Information - CPU, Memory, etc...
3. Agent Top Level Controls.
4. Agent & Server Monitoring Controls & Reporting.
5. Dedicated Server Controls & Status.
6. Agent Activity Logs.

There may be more as this software evolves.

### Agent Details

This is a summary section repeating to the user what agent is being displayed.  This is the name, hostname, owner,
share counts, etc...

This information is static and only updates if the user refreshes the page.

### Platform Information

The left hand side bar shows platform information about the agent.  Some of the information is OS Type, CPU info,
Memory Info, etc...

This information is static and only updates if the user refreshes or updates the page.

### Agent Top Level Controls

Top level agent-wide controls go with the top-right green button.  The button itself says "Update".  Clicking this
button will allow the user to refresh the information on the page without reloading the page in their web browser.

Next to the "Update" button is a drop down menu with 3 dots.  This is the menu, which contains:

1. Agent Membership: Clicking this button will show the membership section, which in turn shows the groups and friends
   the agent is shared with.  This is where the user has the option to remove groups or friends, respectively.

### Agent & Server Monitoring Controls & Reporting.

The monitoring section shows a drop down. The default is the "Agent Health" Monitor.  This is the section where users
may enable monitors and configure them.  The dropdown allows the user to switch between the monitor types.

Use of Agent & Server Monitors deserves its own section, so please navigate to the [Section on Monitors](./monitors.html#agent-server-monitoring)
for that information.

### Dedicated Server Controls & Status.

A table of all installed dedicated servers appears.  It will show the following:

* Game Server Name.
* Last Time the server was updated.
* The build id of the server.
* The build branch of the server.
* Server Status.
* Manual Actions.

#### Server Statuses

Server status show what the state of the dedicate server on the agent is.  The status are:

1. Shutdown - Yellow - Meaning the user has intentionally shut down the server.
2. Online - Green - Meaning the user has intentionally started the server and it is verified to be running.
3. Offline - Red - Meaning the serer is not running when it should be.

#### Manual Actions

The user may also, for each server, take some manual actions:

1. Startup Server - The user may command the server to startup.
2. Update Server - The user may command the agent to update the server software. This only appears if the server
   is not currently running.
3. Shutdown Server - The user may command the server to shutdown.
4. Restart Server - The user may command the server to shutdown and then start back up.  This only appears if
   the server is currently running.

### Agent Activity Logs.

When sharing management duties with different people, knowing who did what and when is useful for governance.  On the
agent information page, the most recent 3 activity logs appear.  The user may click "View All" to see everything that is
currently happening.

Additionally, when viewing all logs the owner has the option to clear out the logs.  Only the agent owner may
clear out log history.

Logs may also show automated events that have happened, in which case there is no user that took the action.  The difference
between the two is made clear.
