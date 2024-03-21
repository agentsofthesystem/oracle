# Software Development Process

## How to run software tests

1. Before code submission run: coverage run -m pytest  (All tests must pass)
2. Create a Pull Request
3. Wait for GitHub actions to run to completion.

## Debugging

This section will speak toward using VSCode for debugging.  A launch configuration is a named JSON object that VSCode
uses to start up a debug session.  There are two relevant to debugging:

1. "Python: Server" - Run this to get a debug session for the backend Flask Server
2. "Python: GUI" - Run this to get a debug session for the frontend PyQt GUI.

The user may use one or the other, or both at the same time.

NOTES:
   - **DO NOT** use print statements to write variables to the terminal in as opposed to proper debugging and expect
     that to get merged!
   - I'm not going to leave instructions for which buttons to click on VSCode to use the debugger.

## Software Testing

This software uses the coverage and pytest python packages for a testing framework.  All tests are in the "tests" folder,
and are split up by unit tests and functional tests.  Any unit test is a simple test of a singular function or independent
object.  A functional or system test would be a test that covers and end-to-end function; eg installing a game server and
seeing that the game shows up in the quick action menu, for example.

For more information about testing plans for Agent Smith, [please read here](../agent_smith/testing.md)
