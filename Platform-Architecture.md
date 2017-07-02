The platform is separated into multiple projects:

NitroxModel - A basic library containing components common to the client and server.  An example is the different packets sent between the two.

NitroxClient - Library that is used directly by Subnautica.  Contains monobehaviours, tcp client, and packet handlers.

NitroxServer - Core server application that manages Nitrox players.

NitroxPatcher - Library that is injected into Subnautica.  Handles modifying internal data structures and bootstrapping the client.

ClientTester - Dummy application that leverages NitroxClient to connect to the server and send simple requests.  Only used for testing purposes. 