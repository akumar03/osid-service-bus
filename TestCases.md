Not everyone will be familiar with the Filing OSID - it is one of the less used interfaces.  Some test cases are needed to establish the design patterns needed to flesh out a service bus implementation of the OSIDs.

## Case 1 - Login ##

A user enters a user name and password.
These credentials are used by the AuthenticationManager to authorize access to the system for that user.  An authorization is returned.

When  multiple authentication servers are present, several approaches are possible:

  1. Use a specified server
  1. Try servers in a specified order
  1. Federate with no order


## Case 2 - Get User Metadata ##

Given an authenticated agent, get metadata associated with it.


## Case 3 - Get Files from File System ##

> In a simple use case, the application wants to get a list of directories at the root of the file system.  The following steps are used:

  1. Get an OsidRuntimeManager.
  1. Get a FilingManager that implements the OSID bus.
  1. Get a DirectoryEntryLookupSession from the FilingManager.
  1. Get the directories.

It’s in the last step that some magic happens.  Rather than accessing the local file system, a message is created and sent to the server (how is the server specified?).  Enough information needs to be provied in the message that the remote endpoint can  access the server file system via another FilingManager implementation.

At a minimum, the message must contain the following information:

  1. Server destination
  1. Path to a directory
  1. View (Federated, Isolated, etc.)

If no server destination is specified, the local system is assumed.
If no path is given, the root is assumed.
If no view is specififed, isolated view is assumed.

## Case 4 - Get an Asset from Repository ##




# Introduction #

Add your content here.


# Details #

Add your content here.  Format your content with:
  * Text in **bold** or _italic_
  * Headings, paragraphs, and lists
  * Automatic links to other wiki pages