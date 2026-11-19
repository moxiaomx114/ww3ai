# WW3AI Air Combat Mod

[简体中文](README.md) · English

WW3AI is a Minecraft add-on for McWW3. It gives aircraft AI pilots that can fly in formation and fight. Spawn a wingman to fly alongside you, or set up two sides on the map and watch them fight. The built-in scripts work out of the box. You can also assign a language model to a team.

This page describes the bilingual release. The in-game version still reads `1.0.0`.

[Download WW3AI](https://github.com/moxiaomx114/ww3ai/releases) · [Bilingual player manual](docs/WW3AI-Player-Manual-ZH-EN.pdf)

## Install

This build was tested with **Minecraft Java 1.20.1, Forge 47.4.29 and McWW3 2.1-beta**. You also need a version of Distant Horizons that works with your McWW3 setup.

| Requirement | Where to get it |
| --- | --- |
| Minecraft Java 1.20.1 | Minecraft Launcher |
| Forge 47.4.29 | [Forge downloads](https://files.minecraftforge.net/net/minecraftforge/forge/index_1.20.1.html) |
| McWW3 2.1-beta | [McWW3 downloads](https://mcww3.com/download) |
| Distant Horizons | [Modrinth](https://modrinth.com/mod/distanthorizons). Pick a Forge build compatible with your setup. |

1. Close the game. On GitHub Releases, find the bilingual release and download **ww3ai-bilingual-tools.jar** from its assets.
2. Put the JAR in your game instance’s `mods/` folder. If you’re upgrading, move the old WW3AI JAR out first. Keep one copy per instance.
3. Launch the Forge instance and press **G** in a world. The console starts in Simplified Chinese. Click **EN** in the upper-right corner to switch to English.

The repository’s `mods/ww3ai-1.0.0.jar` has the same contents as this release’s `ww3ai-bilingual-tools.jar`.

For multiplayer, use the same WW3AI release on the client and server. Some team and model settings require OP permissions on dedicated servers. The squadron deployer requires OP level 2.

## Try these in game

| What you want to do | Where to find it |
| --- | --- |
| Spawn a wingman or an enemy | Press **G** to open the console. You can also create teams, set relations, and toggle AI and weapons fire. |
| Change wingman orders or formation | Press **H** to cycle wingman orders or **J** to open the formation editor and adjust slots. |
| Place one aircraft | In Creative mode, find the purple-and-black **Air Combat Deployer** under **Tools & Utilities**. Hold it and right-click. Choose an aircraft, team and loadout, then pick a point on the map. Give the aircraft an AI pilot or park it to fly yourself. |
| Deploy several squads | In the same tab, find the **WW3 Squadron Deployer**. A plan can have up to eight squads, with one to five fixed-wing aircraft per squad. Save the plan or confirm to deploy the whole batch. |

To reuse a loadout, save a blueprint in the Air Combat Deployer’s **Loadout / Blueprints** screen. In the squadron deployer, select that blueprint for a squad using the same aircraft type.

### Set up a 5v5

Close the game or stop the server. Edit these two settings under `[general]` in the host’s `config/ww3ai-common.toml`, then start it again.

    targetPlayersOnly = false
    maxVehicles = 12

The default cap is eight. A 5v5 needs at least ten free AI slots. Back in the world, turn on AI and weapons fire in the **G** console and set the side mode to **WW3 relations**. Load the **5v5 preset** in the squadron deployer and check the aircraft positions and heights. Keep **Hostile** on, then click **Deploy All**. The Hostile option changes the affected teams’ relations in that world.

### Give teams different models

In **G → Models**, add an OpenAI-compatible or Ollama provider. Fetch the list, select the models you want and save the provider. Enable the provider and the global models switch. Go to **G → Team Ctrl**, select a team, choose **LLM Tactics** and a model, then click **Apply to Team**. Repeat for the other team. Choose **Script Only** for teams that should use the built-in rules. Your provider may charge for connection tests and model requests.

## Useful commands

| Command | What it does |
| --- | --- |
| `/give @s ww3ai:deployer` | Gives you the Air Combat Deployer |
| `/give @s ww3ai:batch_deployer` | Gives you the WW3 Squadron Deployer |
| `/ww3ai menu` | Opens the console |
| `/ww3ai status` | Shows AI status |

`/give` requires cheats or OP permissions. The bilingual player manual linked above has the full instructions.

When opening an [issue](https://github.com/moxiaomx114/ww3ai/issues), include your game and mod versions, steps to reproduce the problem, and the relevant log excerpt. Remove API keys and other credentials before posting logs.

## About the project

WW3AI is a third-party add-on for McWW3. The main development was done by hy4＋ds4.1f. Review and improvements were completed by gpt6.1sol. This repository publishes the WW3AI JAR and documentation. WW3AI is released under the [MIT License](LICENSE). Get McWW3, Distant Horizons and other dependencies from their own release pages.
