Please be aware that this mod is in it's early stages of development, and that the steps below are to set up a *development environment* for Nitrox. These steps are **not** for a regular install of this mod. We discourage the use of this mod for casual play until a stable public release has been made.

1. Pull git repository locally (pass `--recursive` to `git clone` to init and clone submodules).(git clone https://github.com/SubnauticaNitrox/Nitrox.git/ --recursive)
2. Initialize git submodule(s) by running the following command: `git submodule update --init --recursive`. This command can also be used to fetch and update changes.
3. Load `.sln` inside visual studio
4. Build entire solution to generate binaries
    - If your Subnautica installation folder is not located in the usual folder (`C:\Program Files (x86)\Steam\steamapps\common\Subnautica`), a file called `DevVars.targets` will be generated in the solution directory where an alternative path can be set up. If this file is present, this location will be used regardless of the usual folder.
5. Inject `NitroxPatcher` into `Assembly-CSharp`:
    1. Load up [dnspy](https://github.com/0xd4d/dnSpy)
    2. Find a suitable method that gets executed before the actual game starts (`GameInput.Awake()` for instance)
    3. open the method editor (<kbd>ctrl</kbd>+<kbd>shift</kbd>+<kbd>e</kbd> when your cursor is somewhere in this method)
    4. Add a reference to `NitroxPatcher` (bottom-left corner, open button). This should be in the same directory as `Assembly-CSharp`. If not, follow step 3 more carefully.
    5. Inject startup code: `NitroxPatcher.Main.Execute()`.
6. Start Subnautica
7. Verify Subnautica logs at `Subnautica/Subnautica_Data/output_log.txt` (Search for `nitrox`, verify no errors)
8. Run NitroxServer project and verify that there are no errors
9. In client, join a new game and type in the console command `mplayer playername [ip]` (defaults to localhost), or connect through the UI.