# How do I setup Nitrox?
1. Pull git repository locally
2. Load .sln inside visual studios
3. Resolve any missing dependencies(Assembly-CSharp.dll) 
- These are missing from the repo intentionally.  DO NOT commit these here.
4. Build entire solution to generate binaries
5. Copy NitroxModel, NitroxClient, and NitroxPatcher to Subnautica/Subnautica_Data/Managed
6. Inject NitroxPatcher into Assembly-CSharp... dnspy works well.
7. Run NitroxServer project
8. Start Subnautica and enter a new game
9. Type in the console command "mplayer <name> <OPTIONAL ip>"
10. Validate server console output

