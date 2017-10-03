Please be aware that this mod is in it's early stages of development, and that the steps below are to set up a *development environment* for Nitrox. These steps are **not** for a regular install of this mod. We discourage the use of this mod for casual play until a stable public release has been made.

1. Pull git repository locally
2. Load `.sln` inside visual studio
3. Build entire solution to generate binaries
    - If your Subnautica installation folder is not located in the usual folder (`C:\Program Files (x86)\Steam\steamapps\common\Subnautica`), a file called `DevVars.targets` will be generated in the solution directory where an alternative path can be set up. If this file is present, this location will be used regardless of the usual folder.
4. Inject `NitroxPatcher` into `Assembly-CSharp`:
    1. Load up [dnspy](https://github.com/0xd4d/dnSpy)
    2. Find a suitable method that gets executed before the actual game starts (`GameInput.Awake()` for instance)
    3. Add a reference to `NitroxPatcher` (in the 'edit method' window, left bottom corner buttons). This should be in the same directory as `Assembly-CSharp`. If not, follow step 3 more carefully.
    4. Inject startup code: `NitroxPatcher.Main.Execute()`.
5. Start Subnautica
6. Verify Subnautica logs Subnautica/Subnautica_Data/output_log.txt (Search for nitrox / verify no errors)
7. Start server instance of subnautica (regular instance of subnautica with targets -server [optionally -nographics -batchmode]) creating a shortcut is recommended.
8. Verify no errors when starting server.
9. In client, join a new game and type in the console command `mplayer playername [ip]` (defaults to localhost)

