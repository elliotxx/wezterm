<h2 align="center">My WezTerm Config</h2>

<p align="center">
  <a href="https://github.com/KevinSilvester/wezterm-config/stargazers">
    <img alt="Stargazers" src="https://img.shields.io/github/stars/KevinSilvester/wezterm-config?style=for-the-badge&logo=starship&color=C9CBFF&logoColor=D9E0EE&labelColor=302D41">
  </a>
  <a href="https://github.com/KevinSilvester/wezterm-config/issues">
    <img alt="Issues" src="https://img.shields.io/github/issues/KevinSilvester/wezterm-config?style=for-the-badge&logo=gitbook&color=B5E8E0&logoColor=D9E0EE&labelColor=302D41">
  </a>
  <a href="https://github.com/KevinSilvester/wezterm-config/actions/workflows/lint.yml">
    <img alt="Build" src="https://img.shields.io/github/actions/workflow/status/KevinSilvester/wezterm-config/lint.yml?&style=for-the-badge&logo=githubactions&label=CI&color=A6E3A1&logoColor=D9E0EE&labelColor=302D41">
  </a>
</p>

![screenshot](./.github/screenshots/wezterm.gif)

---

### Features

-   [**Background Image Selector**](https://github.com/KevinSilvester/wezterm-config/blob/master/utils/backdrops.lua)

    Uses `wezterm.read_dir` to scan the `backdrops` directory for images.

    > See: [key bindings](#background-images) for usage

-   [**GPU Adapter Selector**](https://github.com/KevinSilvester/wezterm-config/blob/master/utils/gpu_adapter.lua)

    > :bulb: Only works if the [`front_end`](https://github.com/KevinSilvester/wezterm-config/blob/master/config/appearance.lua#L8) option is set to `WebGpu`.

    A small utility to select the best GPU + Adapter (graphics API) combo for your machine.

    GPU + Adapter combo is selected based on the following criteria:

    1.  <details>
        <summary>Best GPU available</summary>

        `Discrete` > `Integrated` > `Other` (for `wgpu`'s OpenGl implementation on Discrete GPU) > `Cpu`
        </details>

    2.  <details>
        <summary>Best graphics API available (based off my very scientific scroll a big log file in Neovim test 😁)</summary>

        > :bulb:<br>
        > The available graphics API choices change based on your OS.<br>
        > These options correspond to the APIs the `wgpu` crate (which powers WezTerm's gui in `WebGpu` mode)<br>
        > currenly has support implemented for.<br>
        > See: <https://github.com/gfx-rs/wgpu#supported-platforms> for more info

        -   Windows: `Dx12` > `Vulkan` > `OpenGl`
        -   Linux: `Vulkan` > `OpenGl`
        -   Mac: `Metal`

        </details>

---

### Installation
On MacOS:
```bash
brew tap homebrew/cask-fonts
brew install --cask font-fira-code
git clone https://github.com/elliotxx/wezterm-config.git ~/.config/wezterm
```

On Windows:
```bash
scoop bucket add nerd-fonts
scoop install firacode
git clone https://github.com/elliotxx/wezterm-config.git ~/.config/wezterm
```

References:
- https://github.com/tonsky/FiraCode/wiki/Installing

### All Key Binbdings

Most of the key bindings revolve around a <kbd>SUPER</kbd> and a <kbd>SUPER_REV</kbd>(super reversed) keys.<br>

-   On MacOs:
    -   <kbd>SUPER</kbd> ⇨ <kbd>Super</kbd>
    -   <kbd>SUPER_REV</kbd> ⇨ <kbd>Super</kbd>+<kbd>Ctrl</kbd>
-   On Windows and Linux
    -   <kbd>SUPER</kbd> ⇨ <kbd>Alt</kbd>
    -   <kbd>SUPER_REV</kbd> ⇨ <kbd>Alt</kbd>+<kbd>Ctrl</kbd>

> To avoid confusion when switching between different OS and to avoid conflicting<br>
> with OS's built-in keyboard shortcuts.

-   On all platforms: <kbd>LEADER</kbd> ⇨ <kbd>SUPER_REV</kbd>+<kbd>Space</kbd>

#### Miscellaneous/Useful

| Keys                           | Action                                      |
| ------------------------------ | ------------------------------------------- |
| <kbd>F1</kbd>                  | `ActivateCopyMode`                          |
| <kbd>F2</kbd>                  | `ActivateCommandPalette`                    |
| <kbd>F3</kbd>                  | `ShowLauncher`                              |
| <kbd>F4</kbd>                  | `ShowLauncher` <sub>(tabs only)</sub>       |
| <kbd>F5</kbd>                  | `ShowLauncher` <sub>(workspaces only)</sub> |
| <kbd>F11</kbd>                 | `ToggleFullScreen`                          |
| <kbd>F12</kbd>                 | `ShowDebugOverlay`                          |
| <kbd>SUPER</kbd>+<kbd>f</kbd>  | Search Text                                 |
| <kbd>SUPER</kbd>+<kbd>u</kbd>  | Open URL                                    |
| <kbd>SUPER</kbd>+<kbd>q</kbd>  | Quit Wezterm                                |
| <kbd>Option</kbd>+<kbd>←</kbd> | Backward Word                               |
| <kbd>Option</kbd>+<kbd>→</kbd> | Forward Word                                |

&nbsp;

#### Copy+Paste

| Keys                          | Action               |
| ----------------------------- | -------------------- |
| <kbd>SUPER</kbd>+<kbd>c</kbd> | Copy to Clipborad    |
| <kbd>Ctrl</kbd>+<kbd>v</kbd>  | Paste from Clipborad |

&nbsp;

#### Tabs

##### Tabs: Spawn+Close

| Keys                              | Action                                |
| --------------------------------- | ------------------------------------- |
| <kbd>SUPER</kbd>+<kbd>t</kbd>     | `SpawnTab` <sub>(DefaultDomain)</sub> |
| <kbd>SUPER_REV</kbd>+<kbd>f</kbd> | `SpawnTab` <sub>(WSL:Ubuntu)</sub>    |
| <kbd>SUPER_REV</kbd>+<kbd>w</kbd> | `CloseCurrentTab`                     |

##### Tabs: Navigation

| Keys                              | Action         |
| --------------------------------- | -------------- |
| <kbd>SUPER</kbd>+<kbd>[</kbd>     | Next Tab       |
| <kbd>SUPER</kbd>+<kbd>]</kbd>     | Previous Tab   |
| <kbd>SUPER_REV</kbd>+<kbd>[</kbd> | Move Tab Left  |
| <kbd>SUPER_REV</kbd>+<kbd>]</kbd> | Move Tab Right |
| <kbd>SUPER</kbd>+<kbd>1</kbd>     | Move Tab 1     |
| <kbd>SUPER</kbd>+<kbd>2</kbd>     | Move Tab 2     |
| <kbd>SUPER</kbd>+<kbd>3</kbd>     | Move Tab 3     |
| <kbd>SUPER</kbd>+<kbd>4</kbd>     | Move Tab 4     |
| <kbd>SUPER</kbd>+<kbd>5</kbd>     | Move Tab 5     |
| <kbd>SUPER</kbd>+<kbd>6</kbd>     | Move Tab 6     |
| <kbd>SUPER</kbd>+<kbd>7</kbd>     | Move Tab 7     |
| <kbd>SUPER</kbd>+<kbd>8</kbd>     | Move Tab 8     |
| <kbd>SUPER</kbd>+<kbd>9</kbd>     | Move Tab 9     |

&nbsp;

#### Windows

| Keys                          | Action        |
| ----------------------------- | ------------- |
| <kbd>SUPER</kbd>+<kbd>n</kbd> | `SpawnWindow` |

&nbsp;

#### Panes

##### Panes: Split Panes

| Keys                               | Action                                           |
| ---------------------------------- | ------------------------------------------------ |
| <kbd>SUPER</kbd>+<kbd>\\</kbd>     | `SplitHorizontal` <sub>(CurrentPaneDomain)</sub> |
| <kbd>SUPER_REV</kbd>+<kbd>\\</kbd> | `SplitVertical` <sub>(CurrentPaneDomain)</sub>   |

##### Panes: Zoom+Close Pane

| Keys                              | Action                |
| --------------------------------- | --------------------- |
| <kbd>SUPER</kbd>+<kbd>Enter</kbd> | `TogglePaneZoomState` |
| <kbd>SUPER</kbd>+<kbd>w</kbd>     | `CloseCurrentPane`    |

##### Panes: Navigation

| Keys                              | Action                  |
| --------------------------------- | ----------------------- |
| <kbd>SUPER_REV</kbd>+<kbd>k</kbd> | Move to Pane (Up)       |
| <kbd>SUPER_REV</kbd>+<kbd>j</kbd> | Move to Pane (Down)     |
| <kbd>SUPER_REV</kbd>+<kbd>h</kbd> | Move to Pane (Left)     |
| <kbd>SUPER_REV</kbd>+<kbd>l</kbd> | Move to Pane (Right)    |
| <kbd>SUPER_REV</kbd>+<kbd>p</kbd> | Swap with selected Pane |

&nbsp;

#### Font Size

| Keys                          | Action             |
| ----------------------------- | ------------------ |
| <kbd>SUPER</kbd>+<kbd>=</kbd> | `IncreaseFontSize` |
| <kbd>SUPER</kbd>+<kbd>-</kbd> | `DecreaseFontSize` |

&nbsp;

#### Background Images

| Keys                              | Action                  |
| --------------------------------- | ----------------------- |
| <kbd>SUPER</kbd>+<kbd>/</kbd>     | Select Random Image     |
| <kbd>SUPER</kbd>+<kbd>,</kbd>     | Cycle to next Image     |
| <kbd>SUPER</kbd>+<kbd>.</kbd>     | Cycle to previous Image |
| <kbd>SUPER_REV</kbd>+<kbd>/</kbd> | Fuzzy select Image      |

&nbsp;

#### Key Tables

> See: <https://wezfurlong.org/wezterm/config/key-tables.html>

| Keys                           | Action        |
| ------------------------------ | ------------- |
| <kbd>LEADER</kbd>+<kbd>f</kbd> | `resize_font` |
| <kbd>LEADER</kbd>+<kbd>p</kbd> | `resize_pane` |

##### Key Table: `resize_font`

| Keys           | Action                          |
| -------------- | ------------------------------- |
| <kbd>k</kbd>   | `IncreaseFontSize`              |
| <kbd>j</kbd>   | `DecreaseFontSize`              |
| <kbd>r</kbd>   | `ResetFontSize`                 |
| <kbd>q</kbd>   | `PopKeyTable` <sub>(exit)</sub> |
| <kbd>Esc</kbd> | `PopKeyTable` <sub>(exit)</sub> |

##### Key Table: `resize_pane`

| Keys           | Action                                         |
| -------------- | ---------------------------------------------- |
| <kbd>k</kbd>   | `AdjustPaneSize` <sub>(Direction: Up)</sub>    |
| <kbd>j</kbd>   | `AdjustPaneSize` <sub>(Direction: Down)</sub>  |
| <kbd>h</kbd>   | `AdjustPaneSize` <sub>(Direction: Left)</sub>  |
| <kbd>l</kbd>   | `AdjustPaneSize` <sub>(Direction: Right)</sub> |
| <kbd>q</kbd>   | `PopKeyTable` <sub>(exit)</sub>                |
| <kbd>Esc</kbd> | `PopKeyTable` <sub>(exit)</sub>                |

---

### References/Inspirations

-   <https://github.com/rxi/lume>
-   <https://github.com/catppuccin/wezterm>
-   <https://github.com/wez/wezterm/discussions/628#discussioncomment-1874614>
-   <https://github.com/wez/wezterm/discussions/628#discussioncomment-5942139>
