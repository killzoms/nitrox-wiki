The platform is separated into multiple projects:

### NitroxModel
A basic library containing components common to the client and server.  An example is the different packets sent between the two.

### NitroxClient
Library that is used directly by Subnautica.  Contains monobehaviours, tcp client, and packet handlers.

### NitroxServer
Core server application that manages Nitrox players.

### NitroxPatcher
Library that is injected into Subnautica.  Handles modifying internal data structures and bootstrapping the client. It depends on the Harmony library. 

### NitroxUnity
Asset library for UI/Game components introduced by Nitrox.

### NitroxInstaller
Wix-based MSI installer for Nitrox.

### NitroxInstallerActions
Custom actions for installation, i.e. code injection, firewall rules, etc.

### NitroxTest
Core unit testing project for all of the other projects.

### Harmony
OpenSource library that helps modding games. Allows all kinds of cool stuff to modify original code.

### Lidgren-Network
OpenSource network library that facilitates all networking operations between clients and server.