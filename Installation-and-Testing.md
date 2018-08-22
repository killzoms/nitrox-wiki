# ==== DISCLAIMER ====
**Please be aware that this mod is still in it's early stages of development.  These instructions are for TESTING ONLY.  Please provide detailed bug reports if you choose to install this mod for Subnautica.  We discourage the use of this mod for casual play until a stable public release has been made.<BR>
==== END OF DISCLAIMER ====**

***
These instructions are inspired by a couple of videos explaining installation of this mod.<BR>
{Links to the videos will be added later.}
***

## Software Installation
1. Locate and download software for testing.  Look at this [page](https://github.com/SubnauticaNitrox/Nitrox/wiki/Software-Used-for-Development-&-Installation) for more information.
2. Install Visual Studio 2017 Community version.<BR>
   A. Installation workloads should minimally have ".NET desktop development" and possibly "Desktop development with C++"<BR>
   B. Install the WixToolKit extension
3. Install GetBash {default installation options are fine}
4. Extract dnSpy to a directory for later usage. {feel free to set up links}

***

## Mod Download
1. Use GitBash {"Git CMD" link} to download a current copy of the mod.<BR>
   `git clone --recurse-submodules https://github.com/SubnauticaNitrox/Nitrox.git Documents/Nitrox`<BR>
   This should download to `C:\Users\{user name}\Documents\Nitrox` where {user name} is the current person logged in.<BR>
   If you ever want to re-download using the above command, that directory will need to be deleted and the command run again.
2. In the Nitrox folder {`Documents\Nitrox`}, a _DevVars.targets_ file needs to be created pointing to your Subnautica installation folder.<BR>
   There is a _DevVars.targets.example_ that can be renamed and edited.<BR>
   Contents should look like the following, but pointing to _**your**_ Subnautica installation folder.<BR>
>`<?xml version="1.0" encoding="utf-8"?>`<BR>
`<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">`<BR>
&nbsp;&nbsp;&nbsp;&nbsp;`<PropertyGroup>`<BR>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`<!--Enter the location of your Subnautica installation here:-->`<BR>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`<SubnauticaDir>F:\Steam\steamapps\common\Subnautica</SubnauticaDir>`<BR>
&nbsp;&nbsp;&nbsp;&nbsp;`</PropertyGroup>`<BR>
`</Project>`<BR>
## Mod Compilation
1. Open Visual Studio 2017.<BR>
   _{possibly requires admin mode, not tested without admin mode}<BR>
   If this is the first time you have opened Visual Studio, you can skip signing in, and then choose your default theme._
2. Open the `Documents/Nitrox/Nitrox.sln` file.
3. If everything was done correctly up to this point, the project file should load without errors.<BR>
   _Should you get a message about targeting a specific version of .NETFramework, download and install the targeted pack for the version it wants._
4. Select the `<Build>` item and `<Build Solution>`.
5. It should tell you 7 to 9 items built successfully and possibly a some items updated, but no errors.

***

## Mod installation
1. Open dnSpy.
2. Press `<CTL>+<O>` and open the `Subnautica\Subnautica_Data\Managed\Assembly-CSharp.dll` file.
3. Press `<CTL>+<SHFT>+<K>` for {searching assemblies} for _`GameInput`_
4. Double click on the first "GameInput" of the resulting search.
5. Press `<CTL>+<F>` to find the first instance of _`Awake`_<BR>
   _{This should put you at line 752.}_
6. Select to the right of the bracket on line 753.
7. Press `<CTL>+<SHFT>+<E>` to edit/decompile the subroutine.
8. Press `<CTL>+<O>` to add the assembly reference from file `Subnautica\Subnautica_Data\Managed\NitroxPatcher.dll`
9. Add the following line to the top of the subroutine at line 12.
>  `NitroxPatcher.Main.Execute();`
10. Press the `<Compile>` button at the lower right of the window.
11. Press `<CTL>+<SHFT>+<S>` to save all.

***

## Starting the Server
1. Goto `Documents\Nitrox\NitroxServer\bin\Debug_WPF`
2. Double click on `NitroxServer.exe`

***

# Debug Information
To report a bug / error please give as much detailed information as you can.
1. What the problem is
2. What was happening prior to the bug
3. Server errors if possible
4. Nitrox mod **download date** and **compile date**
5. Subnautica game client version

If the bug is reproducable, a developer will be able to tell you if the following files are necessary for bug analysis.
1. `Documents\Nitrox\NitroxServer\bin\Debug_WPF\save.nitrox`
2. `Documents\Nitrox\NitroxServer\bin\Debug_WPF\UnityEngine.dll`
3. `Documents\Nitrox\NitroxServer\bin\Debug_WPF\UnityEngine.UI.dll`
4. `Documents\Nitrox\NitroxServer\bin\Debug\Poly2Tri.dll`
5. `Documents\Nitrox\NitroxServer\UnityStubs\GameObject.cs`