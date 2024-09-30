# Folder structure

The main Reality2 folder contains several subfolders with code and examples.  These are:

- **apps**
  The main Elixir code for the Reality2 Node.  Here, you can find the inbuilt plugins.

- **cert**
  Symbolic link to the reality2 Web Server cert folder (./apps/reality2_web/priv/cert) with a helpful script for creating new SSL certificates.

- **config**
  More stuff related to the Elixir code for the Reality2 Node.  Don't change things in here unless you know what you are doing.

- **deps**
  The dependencies for the Elixir code for the Reality2 Node.  These are built when you run `./scripts/deps.get`

- **extras**
  A couple of libraries you might need, conveniently located.

- **logos**
  Some possible logos.  Any graphic designers out there want to suggest something better, let me know.

- **scripts**
  Various scripts for running the Reality2 node and making runtime versions.  Switch to this directory before running as some files are created relative to this folder.

- **web**
  The WebApps running on this node.

