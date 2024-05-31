# Agent & Server Monitoring

This section covers all things related to Agent and Dedicated Server Monitoring.

## What are Monitors?

In the context of The Architect, monitors are automated regularly occurring tasks to keep an eye
on your agents and servers.

## Available Monitor Types

There are three types of monitors and each one does something slightly different.  They all share the common
features detailed in that section, but some also have additional settings.

The three monitor types are:

1. Agent Health Monitoring
2. Dedicated Server Health Monitoring
3. Dedicated Server Update Monitoring

### Agent Health Monitoring

The agent health monitor will regularly perform a pulse check on the agent.  If the agent reports an unhealthy
status back to the monitor, then the monitor will create a fault and shut itself down.  The reason for this is
because the entire agent is unreachable or offline.  The agent owner will have to manually get the agent back
online to re-establish a connection.   Once this is done, the user may clear the fault and restart the monitor.

### Dedicated Server Health Monitoring

Dedicated Server Health Monitoring is much like the agent health monitor, but it's specifically interested in the
individual servers running on the agent.  In terms of server health, the check focuses on servers actually being
online when the user expects them to be.  The monitor ignores server which the user has deliberately shutdown.  This
results in checking that the agent can tell whether or not the server is online, which is the responsibility of the
agent to determine.  More simply put, Agent Smith will seek to detect that the server executable can be found on the
host machine.

In the event a server is found to be offline when it should be online, then a fault is generated.  This however, does
not result in the monitor shutting itself down.  This is because it must continue to monitor other dedicate servers. In
this situation, the fault is an alert for the user to clear after fixing the server.

There is a unique setting to this monitor type.  The user may opt to enable a feature where the monitor will attempt to
auto restart a monitor that is found to be offline when it should be online.  The attempt will only be made once and a
fault is still generated so the user knows the attempt was made.

This monitor is also able to detect if the agent itself is entirely offline, much like the Agent Health Monitor, and will
shut itself down in this instance only.

### Dedicated Server Update Monitoring

Dedicated Server Update Monitoring is similar to the Health monitoring but is focused solely on updates. Agent Smith has the
ability to detect when a newer version of the dedicated server is available for download, and this monitor simply queries the agent
for this information.  The update check is done regardless of whether or not a server is online or offline.

In the event a server is found to be in need of an update, then a fault is generated. This however, does
not result in the monitor shutting itself down.  This is because it must continue to monitor other dedicate servers for updates.
In this situation, the fault is an alert for the user to clear after updating the server.

There are two unique settings which can be made for this monitor type:

1. Auto Update: The user may have the monitor attempt to update the server automatically.
2. The final server state: The user may designate whether the monitor should leave the server online, offline, or in the state
   which it was found.  This option only matters when the auto update feature is enabled.

Finally, when the automatic update feature is enabled, the monitor will not just update the server immediately.  That might
potentially disrupt players.  Instead, a the agent owner sets a maintenance hour in their user preferences.  The maintenance
hour is set in the time zone which is also set in preferences.  If the maintenance hours is 12AM midnight, then updates may
only occur automatically between the hour 12AM to 1AM.  When the agent detects for the first time that a server requires an
update, the time may be outside of the maintenance window.  In this case, when alerts are enabled, a notification is given
to all users that it is going to update the server.  Later when the maintenance window comes around, that server will be updated
and again users are updated that this happened.

This monitor is also able to detect if the agent itself is entirely offline, much like the Agent Health Monitor, and will
shut itself down in this instance only.

## Common Features

All monitors have an on/off switch, and a settings menu.  The settings menu is only visible if the agent is running.
Otherwise it is not.

The common features on the settings menu among monitors are:

1. Polling Interval - The user may select 15, 30, or 60 minutes.  This option dicates how often a monitor will perform
   a check.
2. Enable Alerts - This is an on/off option.  When on, monitors will send out an alert whenever a fault is detected.

## More about Monitor Faults

Monitor faults appear on the agent information page in the monitor section.  The user can click an 'x' button to clear them.
Faults also come with alerts to the user if a given monitor has alerts enabled.
