Please be aware that this mod is in it's early stages of development, and that the steps below are to set up a *development environment* for Nitrox. These steps are **not** for a regular install of this mod. We discourage the use of this mod for casual play until a stable public release has been made.

## Required tools
**NOTE** If you know what you're doing you can, of course, pick your own poison. 
1. Visual Studio (Community Edition or otherwise)
2. [DnSpy](https://github.com/0xd4d/dnSpy)
3. [Git](https://git-scm.com/downloads)

### Optional tools
**NOTE** You may need some of these tools depending on your setup. If you're new to programming these are recommended.
1. [SourceTree](https://www.sourcetreeapp.com/)
   This is a visual tool to help with Git. Though it is highly recommended to learn the git commandline.
2. Additional Microsoft .NET components, such as .NET SDK's and .NET targeting packs.
3. Unity if you want to work on visual aspects of the mod/game.
4. SonarLint / Resharper plugin for Visual Studio to help you improve your code quality.

## Development Setup

### Repository setup
1. Fork the repository to your own Github account (use the fork button top-right).
2. Pull git repository locally (pass `--recursive` to `git clone` to init and clone submodules).
   - e.g. `git clone https://github.com/your-github-name/Nitrox.git --recursive`
3. Initialize git submodule(s) by running the following command: 
   - `git submodule update --init --recursive`. This command can also be used to fetch and update changes.

### Nitrox setup
4. Load `Nitrox.sln` inside Visual Studio
5. _If you have Subnautica installed via Steam in the default install location, skip this step._
   1. Open `DevVars.targets.example`
   2. Adjust the line `<SubnauticaDir>C:\Program Files\Epic Games\Subnautica</SubnauticaDir>` to match the location of your Subnautica install directory.
   3. Save the file as `DevVars.targets`
      - *NOTE* If you have this file, it will always use this directory and never use the default steam directory.

6. Build entire solution to generate binaries
7. Inject `NitroxPatcher` into `Assembly-CSharp`:
    1. Load up [dnspy](https://github.com/0xd4d/dnSpy)
    2. Inject before the first line of `GameInput.Awake()`
    3. Add a reference to `NitroxPatcher`. This should be in the same directory as `Assembly-CSharp`. If not, follow step 3 more carefully.
    4. Inject startup code: `NitroxPatcher.Main.Execute()`.
    5. If you get compile errors like in [issue 221](../issues/211) you should be able to remove the offending lines without repercussions.

### Verify setup
8. Start Subnautica
9. If you see a `multiplayer` button Nitrox is correctly loaded.
10. Verify Subnautica logs at `Subnautica/Subnautica_Data/output_log.txt` (Search for `nitrox`, verify no errors)
- **NOTE** There will always be some errors, but nothing substantial in the first part regarding loading of Nitrox.
11. Run NitroxServer project and verify that there are no errors in the console Window
12. In the client, join a new game by connecting through the multiplayer button in the UI.