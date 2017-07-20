1. Pull git repository locally
2. Load .sln inside visual studios
3. Resolve any missing dependencies(Assembly-CSharp.dll) 
- These are missing from the repo intentionally.  DO NOT commit these here.
4. Build entire solution to generate binaries
5. Copy NitroxModel, NitroxClient, and NitroxPatcher to Subnautica/Subnautica_Data/Managed
6. Inject NitroxPatcher into Assembly-CSharp:
* Load up dnspy
* Find a suitable method that gets executed before the actual game starts(StartScreen OnGuiInitialized())
* Inject startup code: NitroxPatcher Main.Execute()
7. Run NitroxServer project
8. Start Subnautica
9. Verify Subnautica logs Subnautica/Subnautica_Data/output_log.txt (Search for nitrox / verify no errors)
10. Type in the console command "mplayer |name| |OPTIONAL ip|"
11. Validate server console output

