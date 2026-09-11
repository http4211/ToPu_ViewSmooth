# ToPu_ViewSmooth

[日本語](README.md) | **English**

[![Blender](https://img.shields.io/badge/Blender-4.2%2B-F5792A?logo=blender&logoColor=white)](https://www.blender.org/)
[![License](https://img.shields.io/badge/License-GPL--3.0--or--later-blue.svg)](#license-and-credits)

**Align the selected edges based on the view.**

## Overview

**ToPu_ViewSmooth** reshapes selected open edge chains as 2D curves in Blender's Mesh Edit Mode. It keeps each chain's endpoints and the selected vertices' depth in the starting view while adjusting their horizontal and vertical positions.

Move the mouse horizontally to adjust **Smoothness**, and use the wheel to adjust **Curve Amount**. Both parameters support negative values.

## Requirements

- Blender 4.2 or later
- Mesh Edit Mode; open, unbranched edge chains with at least 3 vertices
- Japanese / English UI; the add-on preferences overview is always shown in both languages

## Download and installation

1. Download the add-on ZIP from [Releases](https://github.com/http4211/ToPu_ViewSmooth/releases).
2. Keep the ZIP compressed, then drag and drop it into Blender to install it.
3. Alternatively, open `Edit > Preferences > Add-ons`, choose `Install from Disk` from the menu, and select the ZIP.
4. Enable **ToPu_ViewSmooth** in the add-on list.

Use the packaged ZIP containing the `topu_view_curve` folder. This is a legacy-format add-on.

## Location

**3D View > Edit Mode > Right-click > ToPu Tools > ViewSmooth**

Default shortcut: **Ctrl + Alt + C**, configurable in the add-on preferences.

You can also launch **ToPu_ViewSmooth** from the left toolbar, the Edge menu, or F3 search. The ViewSmooth item joins an available ToPu Tools menu; otherwise, the add-on displays its own menu.

## Main features

- Process multiple separate open chains and multiple objects together.
- Support orthographic and perspective views while keeping chain endpoints and selected-vertex view depth.
- Adjust Smoothness and Curve Amount independently from **−1000% to 1000%**.
- Restrict movement to the horizontal or vertical direction through settings.
- Follow mesh X/Y/Z position mirror settings, including multiple axes.
- Show Curve Amount and Smoothness in one row inside a translucent gray panel. Separate Wheel / Mouse Move hint boxes and blue / purple accents identify each control; the last adjusted field is highlighted.
- Recalculate from the starting coordinates so adjustments do not accumulate.

| Parameter | Default | Effect |
| --- | --- | --- |
| Smoothness | 65% | Positive values smooth bends and irregularities. Zero applies no smoothing. Negative values reverse the smoothing displacement to emphasize the original bends. |
| Curve Amount | 100% | Controls the offset from the line between the endpoints. Zero makes the chain straight; 100% keeps the smoothed curve; negative values reverse its bend direction. |

The HUD uses percentages; a property value of `1.0` corresponds to `100%`. **Smoothness 0% and Curve Amount 100% restore the starting shape.** A zero Curve Amount makes the chain straight when both screen directions are enabled; an axis restriction applies only the permitted movement.

## Quick start

1. Enter Mesh Edit Mode and select one or more valid open edge chains.
2. Orient the view to the direction you want to use for the adjustment.
3. Run **ToPu Tools > ViewSmooth** or press **Ctrl + Alt + C**.
4. Adjust the shape using mouse movement and the wheel.
5. **Left-click to confirm, or right-click to cancel and restore the starting coordinates.**

After confirming, use **F9** to adjust the parameters again. Both live adjustment and F9 use the view captured at the start.

## Essential controls

| Input | Action |
| --- | --- |
| Horizontal mouse movement | Adjust Smoothness |
| Mouse wheel | Adjust Curve Amount; 10 percentage points per step |
| Left-click | Confirm |
| Right-click | Cancel and restore the starting vertex positions |

Live adjustment uses mouse movement and the wheel. Set exact values and screen movement restrictions in the tool settings or add-on preferences before starting, or in F9 after confirming.

## Options and limitations

In **Preferences > Add-ons > ToPu_ViewSmooth**, configure the launch shortcut, initial Smoothness, Curve Amount, and screen movement direction. Save preferences when needed to retain shortcut changes.

Closed loops, branched selections, and single edges are skipped. Unselected edges do not count as branches. This tool does not redistribute vertices at equal intervals or add/remove mesh elements.

Mirroring uses existing vertex positions in object-local coordinates, relative to the object origin. **Topology-based mirror matching is not supported.** Missing, ambiguous, or hidden destinations are skipped. The selected side keeps its view depth; the mirrored side may change depth in an oblique view. When both sides are selected, each chain is processed independently.

The current build has not been verified in Blender's GUI or in combination with other add-ons.

## License and credits

Distributed under **GNU General Public License v3.0 or later (GPL-3.0-or-later)**. The full license text is included as `LICENSE` in the add-on ZIP.

- Author: [http4211](https://github.com/http4211)
- Repository: [http4211/ToPu_ViewSmooth](https://github.com/http4211/ToPu_ViewSmooth)
- Copyright (C) 2026 http4211

Please report bugs and feature requests through [Issues](https://github.com/http4211/ToPu_ViewSmooth/issues).
