https://github.com/Vedanshu1/Roblox-Moon/releases

# Roblox Moon Executor — Advanced Script Engine for Roblox 🌙🚀

[![Download Releases](https://img.shields.io/badge/Release-Download-blue?logo=github&style=for-the-badge)](https://github.com/Vedanshu1/Roblox-Moon/releases)
[![Stars](https://img.shields.io/github/stars/Vedanshu1/Roblox-Moon?style=for-the-badge)](https://github.com/Vedanshu1/Roblox-Moon)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](https://github.com/Vedanshu1/Roblox-Moon/blob/main/LICENSE)

![Roblox Moon Banner](https://images.unsplash.com/photo-1451188502541-13943edb6acb?auto=format&fit=crop&w=1400&q=80)

Roblox Moon Executor provides a focused, reliable environment for loading and running custom Lua scripts inside Roblox. It blends a clean UI with a powerful runtime and a script editor. The project targets developers and advanced users who build automation, tools, and custom gameplay experiences within local Roblox sessions.

Table of contents
- Features
- What Roblox Moon Does
- Screenshots and Visuals
- Quick start
- Download and run (Release file to execute)
- Install and setup
- Basic usage
- Script examples
- Built-in API reference
- Editor and workflow tips
- Advanced usage and plugins
- Development and architecture
- Build from source
- Tests and quality checks
- Compatibility and platform notes
- Security model and sandboxing
- Contributing
- Roadmap
- Frequently asked questions
- License

---

## Features

- Lightweight runtime optimized for local Lua execution with Roblox APIs.
- Integrated script editor with syntax highlighting and live logs.
- Cross-session script manager with saved snippets and profiles.
- Hotkeys and quick-inject controls.
- Extensible plugin system for custom tooling.
- Built-in examples and templates for common automation tasks.
- Simple update path via GitHub Releases.

Each feature aims to keep the tool fast and predictable. The UI focuses on the script workflow and on reducing friction when testing and iterating.

---

## What Roblox Moon Does

Roblox Moon launches a controlled local executor environment that talks to a running Roblox client instance. It exposes a set of helpers for script loading, execution, and debugging. The executor provides:

- A place to author and store Lua scripts.
- A runtime that can call Roblox Lua APIs exposed locally.
- Execution control with start, stop, reload, and step-through behavior.
- Logging and variable inspection tools.

You can use Moon to prototype scripts, test game automation logic, or build local utilities around Roblox sessions. The project focuses on developer experience and stable behavior during script runs.

---

## Screenshots and Visuals

Editor view with file list and console:
![Editor View](https://i.imgur.com/6L3O8eG.png)

Live console with colored logs and filter:
![Console View](https://i.imgur.com/3K7YhYk.png)

Script manager with profiles and quick inject:
![Profiles View](https://i.imgur.com/qJ2Y9Qw.png)

Icons and UI use a dark theme tuned for long sessions and code focus.

---

## Quick start

1. Visit the Releases page and download the latest package:
   https://github.com/Vedanshu1/Roblox-Moon/releases

2. Extract the release archive.

3. Run the included executable file from the archive. The release contains a packaged binary tailored for Windows. Look for the executable named `RobloxMoon.exe` in the release assets and run it.

4. Launch Roblox, open a place, and use the Moon UI to inject a script from the editor or a saved profile.

The release page contains the zipped builds and the specific executable that you must run. Locate `RobloxMoon.exe` inside the release assets and execute it.

---

## Download and run (Release file to execute)

Visit the releases page and download the packaged build:
https://github.com/Vedanshu1/Roblox-Moon/releases

The releases page includes the compiled binary and supporting assets. After downloading, extract the archive and run the file named `RobloxMoon.exe`. This file starts the application and opens the editor and console. The UI connects to the local Roblox runtime and waits for a session to accept scripts.

If you keep multiple profiles, store them in the `profiles` folder inside the application directory. Each profile contains saved snippets and hotkey bindings.

---

## Install and setup

Supported platform: Windows (primary). Moon requires a running Roblox client.

Step-by-step:

1. Download the latest release archive from the Releases page. Open the archive and copy its contents to a folder you control, for example: C:\Tools\RobloxMoon

2. Run RobloxMoon.exe from that folder. The app writes local settings to a `config` folder inside the app folder.

3. Open Roblox and load the place you want to test.

4. In the Moon UI, set the target process if needed. Moon auto-detects the Roblox client in most cases. If it does not, use the process selector in Settings to choose `RobloxPlayerBeta.exe`.

5. Load a script and press Run. The console will display logs from the runtime.

Configuration options:
- Start with Windows: toggle in Settings.
- Logging level: Error, Info, Debug.
- Theme: Dark or Light.
- Default scripts folder: set to your scripts repository.

Paths and persistent state live under the app folder so you can move your installation without losing profiles.

---

## Basic usage

Editor layout:
- File tree: left side. Add .lua files here.
- Editor pane: middle. Type scripts and use shortcuts.
- Console: bottom. View runtime logs, errors, and prints.
- Toolbar: top. Buttons for Run, Stop, Inject, Save, Open Profile.

Common tasks:

- Run a script: Open a script in the editor and click Run. The runtime executes the code and logs output in the console.
- Inject: Use Inject to push the script into the running Roblox process without saving or reloading.
- Save as profile: Save a set of scripts and bindings into a profile for later reuse.
- Hotkeys: Assign a hotkey to frequently used scripts.

Shortcuts:
- Ctrl+S: Save
- Ctrl+R: Run
- Ctrl+I: Inject
- Ctrl+Shift+P: Open profile manager

---

## Script examples

Below are sample scripts and patterns that work well with Roblox Moon's API. Each snippet targets common use cases. Use them as templates.

1) Simple print loop

```lua
for i = 1, 5 do
    print("Tick", i)
    wait(1)
end
```

2) Basic player locator

```lua
local players = game:GetService("Players")
local me = players.LocalPlayer
print("Player name:", me.Name)
```

3) Teleport test function

```lua
local lp = game:GetService("Players").LocalPlayer
local hrp = lp.Character and lp.Character:FindFirstChild("HumanoidRootPart")
if hrp then
    hrp.CFrame = CFrame.new(0, 50, 0) -- move above origin
    print("Teleported")
end
```

4) UI overlay template

```lua
local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")
ScreenGui.Name = "MoonOverlay"
ScreenGui.Parent = game:GetService("Players").LocalPlayer:WaitForChild("PlayerGui")
Frame.Size = UDim2.new(0, 300, 0, 100)
Frame.Position = UDim2.new(0.5, -150, 0, 20)
Frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Frame.Parent = ScreenGui
print("Overlay created")
```

5) Event logger (connect to workspace child added)

```lua
workspace.ChildAdded:Connect(function(child)
    print("Child added:", child.Name)
end)
```

Each snippet runs in the client context and interacts with standard Roblox API surfaces.

---

## Built-in API reference

Roblox Moon exposes helper functions on top of the client runtime. These helpers simplify common tasks and reduce boilerplate. The helpers live in the global table `Moon`. Example API:

- Moon.print(msg)
  - Echoes formatted output to the Moon console.

- Moon.run(scriptText)
  - Directly execute a string as a script in the client runtime.

- Moon.loadFile(path)
  - Load a local .lua file from the scripts folder and return the contents.

- Moon.saveProfile(name, data)
  - Save a profile object that includes scripts and bindings.

- Moon.listProfiles()
  - Return an array of saved profiles.

- Moon.inject(scriptText)
  - Inject the provided script into the target Roblox process.

- Moon.setHotkey(keyCombo, scriptId)
  - Bind a script to a hotkey. Pressing the hotkey triggers the script.

- Moon.log(level, msg)
  - Log messages with a level: "INFO", "DEBUG", "ERROR". The console filters by level.

Examples:

```lua
Moon.print("Hello from Moon")
local script = Moon.loadFile("examples/hello.lua")
Moon.inject(script)
```

The helpers call into a small runtime bridge. Use them to manage scripts without manipulating files directly.

---

## Editor and workflow tips

- Use folders to organize scripts by game or by purpose.
- Keep templates for common tasks in a templates folder.
- Save frequently used snippets as profiles for quick injection.
- Use the console filter to hide debug noise when only errors matter.
- Enable live reload for development: changes in the editor can automatically push to the runtime on save.
- Use the built-in snippet manager to store small utilities like print wrappers or formatting helpers.

Editor features:
- Syntax highlighting for Lua.
- Autocomplete for common Roblox API names.
- Error markers for syntax errors.
- Multi-cursor editing.
- Search across scripts.

Profiles let you group multiple scripts and run them together. For example, create a "UI Tools" profile containing a UI overlay script and a logger.

---

## Advanced usage and plugins

Moon supports a plugin system. Plugins extend the editor and runtime features and can add custom UI panels, script transforms, or automation workflows.

Plugin points:
- Editor panel: Add custom panels to show data or controls.
- Preprocess: Transform script text before injection. Useful for macros.
- Postprocess: Modify logs or add handlers for runtime events.
- Tool window: Create floating tools with custom controls.

Sample plugin manifest (JSON):

```json
{
  "name": "AutoFormatter",
  "version": "1.0.0",
  "author": "Dev",
  "entry": "plugins/autofmt/main.lua",
  "permissions": ["editor", "file-system"]
}
```

Plugin runtime:
- Plugins run in a sandbox with access to the Moon API.
- The plugin loader resolves dependencies and enforces a manifest.

Use plugins for:
- Formatting scripts to a style guide.
- Integrating external script libraries.
- Adding telemetry for tests.

---

## Development and architecture

Roblox Moon follows a modular design:

- UI Layer: Electron-based renderer that hosts the editor, file manager, and console.
- Bridge Layer: Native module that talks to the Roblox process and mediates script injection.
- Runtime: The local runtime environment that executes scripts and forwards logs.
- Storage: Profiles, scripts, and settings stored in JSON and local files.

The app uses a small IPC contract between the UI and the native bridge. The contract defines actions such as runScript, inject, listProfiles, and watchFiles.

Key directories:
- src/ui — renderer code and editor components
- src/bridge — native bindings for process operations
- scripts/ — default scripts and templates
- plugins/ — community or local plugins
- test/ — unit and integration tests

Design principles:
- Keep the bridge minimal and focused on process comms.
- Keep the UI reactive and data-driven.
- Isolate plugins from the bridge to limit scope.

---

## Build from source

You can build the project from source. The repository uses Node.js for the UI and a minimal native module for the bridge.

Prerequisites:
- Node.js LTS
- Yarn or npm
- Visual Studio Build Tools (for native bindings)
- Git

Steps:

1. Clone the repository:

```bash
git clone https://github.com/Vedanshu1/Roblox-Moon.git
cd Roblox-Moon
```

2. Install dependencies:

```bash
yarn install
```

3. Build native bridge:

```bash
cd native
node-gyp rebuild
cd ..
```

4. Build UI and package:

```bash
yarn build
yarn package
```

5. The packaged builds appear under `dist/`. Use the packaging scripts to create a release archive.

Follow the build logs if you need to adjust compiler flags or link paths for native modules.

---

## Tests and quality checks

The project includes unit tests for core helpers and integration tests for the editor bridge. Tests run with a test runner and cover:

- Moon helper API
- File IO
- Plugin loader
- Editor syntax checks

Run tests:

```bash
yarn test
```

Continuous integration runs on push and pull requests. The CI ensures builds succeed and tests pass before merges.

Quality tools:
- Linter for Lua and JavaScript
- Prettier for formatting
- Type checks for UI components

---

## Compatibility and platform notes

Primary support: Windows 10 and 11. The bridge uses Windows APIs to locate and interact with the Roblox client. Some parts may work on other platforms, but builds and support focus on Windows.

Roblox Moon targets specific Roblox client versions. The app handles common runtime changes but may require updates if Roblox alters process internals significantly.

Supported Roblox process names:
- RobloxPlayerBeta.exe
- RobloxStudioBeta.exe (limited testing)

If auto-detect fails, set the process in Settings.

---

## Security model and sandboxing

Moon runs scripts in a local context and uses a bridge to the running Roblox client. The app segregates plugin and script execution environments.

- Scripts run with the privileges of the local Roblox client.
- Plugins run in a sandbox with restricted API access.
- The bridge prevents arbitrary file system access from scripts unless allowed by plugin permissions.

You can restrict plugin permissions from Settings. The default configuration limits file system operations to the scripts folder.

---

## Contributing

Contributions help the project expand templates, fix bugs, and add plugins. The repository accepts pull requests on GitHub.

How to contribute:

1. Fork the repo.
2. Create a feature branch: git checkout -b feat/your-feature
3. Add tests and docs.
4. Open a pull request with a clear description of changes.

Guidelines:
- Keep PRs focused and small.
- Include tests for logic changes.
- Use descriptive commit messages.

Areas that welcome contribution:
- Templates and example scripts
- Plugin examples
- Editor features like refactorings or search enhancements
- Bridge stability and process detection

---

## Roadmap

Planned items:
- Plugin marketplace and discovery
- Cross-platform bridge support
- Enhanced inspector for runtime objects
- Script dependency manager
- Built-in diff and versioning for scripts
- Community templates and shared profiles

Roadmap items appear in the repository issues and project board. Follow the board to track progress and join discussions.

---

## Frequently asked questions

Q: Where do I get the app?
A: Download the packaged build from the Releases page:
https://github.com/Vedanshu1/Roblox-Moon/releases

Q: Which file do I run?
A: The release assets include a packed installer or a zipped bundle. Extract the archive and run `RobloxMoon.exe`. The release page lists the binary inside the assets.

Q: Can I run it on macOS or Linux?
A: The project targets Windows. Some UI pieces may run cross-platform, but the bridge depends on Windows APIs.

Q: What scripts does Moon support?
A: Any Lua script that uses Roblox client APIs. The editor highlights and validates standard Roblox API names.

Q: Does Moon alter Roblox files?
A: Moon does not modify Roblox installation files. It interacts with the running client at runtime. Settings and profiles live in the app folder only.

Q: Can I create plugins?
A: Yes. Use the plugins folder and manifest format. Plugins run in a sandboxed environment and use the Moon API.

Q: How do I report bugs?
A: Open an issue on the GitHub repository and include logs from the console and steps to reproduce.

Q: How do I update?
A: Check the Releases page periodically. Download the new release asset, extract, and replace the old files.

---

## Example workflows

1) Rapid iterate on UI changes:
- Create a UI overlay template in the editor.
- Enable live reload.
- Modify code and save. Moon injects the update immediately.

2) Multi-script profiles:
- Create a profile that includes a logger, overlay, and input mapper.
- Save the profile and bind it to a hotkey.
- Activate the profile in-game to set up the environment.

3) Plugin-driven automation:
- Install a plugin that transforms shorthand macros into full scripts.
- Use the plugin to expand scripts and inject them.

Each workflow leverages profiles, hotkeys, and the plugin system to speed common tasks.

---

## Example project: Tooling Pack

Structure:

- templates/
  - overlay.lua
  - logger.lua
  - utils.lua
- profiles/
  - UI-Toolset.json
  - Debugger.json
- plugins/
  - formatter/
    - main.lua
    - manifest.json

A user can clone the tooling pack into the scripts folder and load a profile named UI-Toolset in Moon. The profile runs overlay.lua and logger.lua in sequence. The formatter plugin cleans up code before injection.

---

## API extension ideas

- Moon.fetchRemote(url) — fetch remote snippets and cache them locally.
- Moon.syncProfiles(gitRepo) — synchronize profiles with a Git repo for sharing.
- Moon.recordSession(file) — record logs and events into a session file for replay.

These extensions improve sharing and collaboration for teams that build and test local Roblox logic.

---

## Tests and sample cases

Include test cases to validate the bridge and helpers:

- helper_print_sanity — ensure Moon.print prints to console.
- loadfile_exists — verify Moon.loadFile returns expected content.
- plugin_manifest_parsing — ensure the plugin loader handles valid and invalid manifests.
- session_injection_flow — integration test for inject and run cycles.

Automated tests run in CI on push and PRs.

---

## License

This project uses the MIT license. See LICENSE file for full terms.

---

Thank you for checking this repository. For downloads and the release binary, visit the Releases page and run the included executable:
https://github.com/Vedanshu1/Roblox-Moon/releases

Support, issues, and contributions welcome via GitHub issues and pull requests.