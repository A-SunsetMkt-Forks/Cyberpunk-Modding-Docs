---
description: Things I wish I had known before I jumped into Blender
cover: ../../../.gitbook/assets/blender_massacre_title_picture.png
coverY: 0
---

# Blender: Getting Started

Summary

**Published:** May 11 2024 by [manavortex](https://app.gitbook.com/u/NfZBoxGegfUqB33J9HXuCs6PVaC3 "mention")\
**Last documented update:** Feb 17 2025 by [manavortex](https://app.gitbook.com/u/NfZBoxGegfUqB33J9HXuCs6PVaC3 "mention")

{% hint style="success" %}
**TL;DR:** Blender hard, but Blender free and Thog will make 3d object.&#x20;

Do yourself a favour and&#x20;

* read at least [#general-tips](./#general-tips "mention") from this page
* optional: complete the Blender Donut Tutorial (find latest version via websearch)&#x20;
{% endhint %}

The open source software [Blender](https://www.blender.org/download/) is huge and intimidating — it is a tool for professionals, and many people consider it as good or even better than paid alternatives.

While it has a steep learning curve, **everyone** can dabble in Blender (even you! Even your mom!). This page will give you tips that'll make it easier for you.

{% hint style="info" %}
Blender is **not intuitive** to use (perhaps if your knees bend backwards). Our guides usually tell you what to click and teach you keyboard shortcuts. On top of that, [#customizing-the-interface](./#customizing-the-interface "mention") is easy and you should definitely do it!
{% endhint %}

## Interface

### Overview

This is Blender's interface. The main action happens in the **Viewport**. In the default perspective (**Layout**), it is on the left — you can switch **perspectives** (workspace layouts) by using the perspective selector (purple) on the file bar.

Read [#navigating-the-viewport](./#navigating-the-viewport "mention") for how to move around in it.

<figure><img src="../../../.gitbook/assets/blender_UI_guide_1.png" alt=""><figcaption></figcaption></figure>

### General tips

1. **Use keyboard shortcuts** - they will speed things up by at least 70%. Put a post-it on your monitor and only remove it when you know them by heart.
   * See [#keyboard-shortcuts-global](./#keyboard-shortcuts-global "mention") below for a list
   * See [#customizing-the-interface](./#customizing-the-interface "mention") for how to create custom shortcuts (it's easy and you should do it)
2. That being said, **use the** [**Search Menu**](https://blender.stackexchange.com/questions/141118/how-to-access-the-search-menu-2-8-used-to-be-spacebar-in-2-79) (Hotkey: `F3` or `Space`, depending on your settings) . \
   It gives you access to all of Blender's functions! Click on the link to see it in action
3. The main action happens in your `Viewport` (the big one on the left).&#x20;
   * You can use the Perspective Selector (pink) to swap around custom-defined workspaces.
   * Check [#customizing-the-interface](./#customizing-the-interface "mention") for more detes.
4. Understand when to use **Object Mode** and when to use **Edit** or **Pose** Mode.  Read [#view-port-modes](./#view-port-modes "mention") for more detes.
   * You can switch between Edit Mode and Object Mode with `Tab` (turquoise dropdown on screenshot 1)
5. You can switch the current selection tool with a long click on the tool's surface (shortcut to cycle: `W`)
6. You can (de)select multiple things by ctrl-clicking on them.&#x20;
7. The most recently selected thing is called **`Active`** (this shows up in many context menus)
   * The **Select Circle** tool does not set an **Active** selection.
8. You can toggle **X-Ray mode** (Shortcut: `Alt+Z`) by clicking the purple icon in the screenshot above
9. You can hide things (Shortcut: `H`), Unhide them (Shortcut: `Alt+H`), or hide everything else (Shortcut: `Shift+H`)
10. You can undo your last action (Shortcut: `Ctrl+Z`), and redo an action (Shortcut: `Ctrl+Shift+Z`)

### Navigating the viewport

* **Spin** the viewport by pressing the `middle mouse button` and moving the mouse
* Zoom with the `mouse wheel`
* With `/` (Numpad Divide), you activate `Local Mode`, which will show you only your selection
* Press `Numpad 5` to toggle between `perspective` and `orthographic` mode. Try around with them

### Customizing the interface

{% hint style="info" %}
Don't be shy to do this! If you fuck up, you can always restore the default settings!
{% endhint %}

You can easily customize the interface — for example, you can **set custom keyboard shortcuts** by simply right-clicking on something!

<figure><img src="../../../.gitbook/assets/blender_custom_keyboard_shortcut.png" alt="" width="223"><figcaption><p>When you use something a lot, give it a shortcut.</p></figcaption></figure>

#### Save Startup File

To make your changes persistent, save your current .blend under `File -> Defaults -> Save Startup File`.

<figure><img src="../../../.gitbook/assets/blender_save_startup_file.png" alt=""><figcaption></figcaption></figure>

### View port modes

You switch the View Mode in the **dropdown on the topleft**. Depending on your **perspective**, there are multiple options:

<figure><img src="../../../.gitbook/assets/blender_mode_selection.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
You can switch between the most commonly used modes, **Object** and **Edit,** with `Tab`.
{% endhint %}

Here's what they do:

<table><thead><tr><th width="201"></th><th></th></tr></thead><tbody><tr><td>Object Mode</td><td>This is where you switch the active 3d object. The other modes only work on the current selection.<br>Read <a data-mention href="./#object-mode">#object-mode</a> below for more detes.</td></tr><tr><td>Edit Mode</td><td>Lets you alter the objects 3d data by moving pixels around. Read <a data-mention href="./#edit-mode">#edit-mode</a> below for more detes.</td></tr><tr><td>Pose Mode</td><td>Only available when you have an <strong>armature</strong> (rig, skeleton) selected. This is where you <a href="../../../modding-guides/animations/animations/poses-animations-make-your-own/">make poses</a>.</td></tr><tr><td>Sculpt Mode</td><td><strong>You usually don't need this!</strong><br>Sculpt the mesh as if it's clay. Requires you to <strong>delete shapekeys</strong>, and leads to bad topologies. Proportional Editing is much better.<br><em>See =></em> <a data-mention href="../mesh-sculpting-techniques/">mesh-sculpting-techniques</a><em>.</em></td></tr><tr><td>Vertex Paint</td><td>Lets you create Vertex Paint Data. You only need this for <a href="../garment-support-how-does-it-work/#painting-your-parameters">custom garment support</a> (so as a beginner, stay away from it)</td></tr><tr><td>Weight Paint</td><td>Weights determine how an object moves with the armature. Everyone hates it, but you can usually get around weight painting by simply <a href="../porting-3d-objects-to-cyberpunk.md#step-4-weight-transfer">stealing weights</a> from an in-game item.</td></tr><tr><td>Texture Paint</td><td>"We have <a href="https://www.adobe.com/products/substance3d/apps/painter.html">Adobe Substance Painter</a> at home!" It's free, it's 3d, but using it sucks. Before switching to Substance Painter, I painted in photoshop and used it just for positioning/rough guidelines.</td></tr></tbody></table>

### Keyboard Shortcuts (global)

The shortcuts below are shared between Object and Edit mode:

<table><thead><tr><th width="192"></th><th></th></tr></thead><tbody><tr><td><code>H</code></td><td>Hide selected elements</td></tr><tr><td><code>Shift+H</code></td><td>Hide everything <strong>except for</strong> the selected elements</td></tr><tr><td><code>Alt+H</code></td><td>Un-hide everything</td></tr><tr><td><code>X</code></td><td>Delete selection</td></tr><tr><td><code>Ctrl+I</code></td><td>Invert selection</td></tr><tr><td><code>Shift+D</code>, <code>Click</code></td><td>Duplicate selection</td></tr></tbody></table>

## The 3d Cursor

In **Object**, **Edit** and **Pose** Mode, you can use the 3d cursor (`Shift-Click` or `Shift-right click`, depending on your settings). You can use it as a [#pivot-point](./#pivot-point "mention") or just as an orientation mark.

This is especially handy in combination with Snap Selection:

<figure><img src="../../../.gitbook/assets/blender_snap_selection.png" alt=""><figcaption><p>Snap Selection - move things around via 3d cursor!</p></figcaption></figure>

## Object Mode

Object mode is where you select stuff that you want to edit.

{% hint style="info" %}
If you move anything in Object Mode, you need to Apply Transforms (Object -> Apply -> All Transforms), or Cyberpunk will ignore your changes.
{% endhint %}

## Edit Mode

Edit mode is where you actually **edit** the mesh.

{% hint style="info" %}
You can only edit things that are selected in Object Mode.

Read [#selection-tricks](./#selection-tricks "mention") on how to make your way around this!
{% endhint %}

<figure><img src="../../../.gitbook/assets/blender_UI_guide_2.png" alt=""><figcaption></figcaption></figure>

### Editing tricks

{% hint style="info" %}
You only edit the current selection (read [#selection-tricks](./#selection-tricks "mention") on how to get one).

Check [#pivot-point](./#pivot-point "mention") to change your operation's origin.
{% endhint %}

With any active selection, you can toggle the following actions by hotkey, and then move the mouse:

* Scale (Hotkey: `S`): Grow or shrink something
* Rotate (Hotkey: `R`) What it says
* Move (Hotkey: `G`) Reposition something

{% hint style="success" %}
**You can lock each of those operations on an axis!**&#x20;

For example, press `G` -> `Z` to move your selection up and down. Press Z again to remove the lock.
{% endhint %}

#### Pivot Point

By pressing `.`, you can change the current `Pivot Point:`

<figure><img src="../../../.gitbook/assets/image (422).png" alt="" width="375"><figcaption></figcaption></figure>

This is the **origin** for your transforms:

<figure><img src="../../../.gitbook/assets/blender_pivot.png" alt="" width="375"><figcaption></figcaption></figure>

Read [#the-3d-cursor](./#the-3d-cursor "mention") on how to make use of the little dude.

### Selection tricks

#### Selection Mode

With the shortcuts `1`, `2` and `3`, you can switch the Selection Mode between [`Vertex`](#user-content-fn-1)[^1], [`Edge`](#user-content-fn-2)[^2], and [`Face`](#user-content-fn-3)[^3]:

<figure><img src="../../../.gitbook/assets/blender_addon_select_mode.png" alt=""><figcaption></figcaption></figure>

There are a couple more modes that can come in handy when you're using the UV Editor.

<figure><img src="../../../.gitbook/assets/Screenshot 2025-01-12 165349.png" alt=""><figcaption><p>Standard location</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image_2025-01-12_170852487.png" alt=""><figcaption><p>Editing location </p></figcaption></figure>

The first one (highlighted in blue in the first image) is the standard select mode. The second one will be your friend, the extend mode, which lets you extend your existing selection  or start a new selection while your previous selection stays put. This is not possible with the standard select mode as it would overwrite the previous selection.

<figure><img src="../../../.gitbook/assets/image_2025-01-12_171512854.png" alt=""><figcaption><p>Creating a seperate selection in UV Editor</p></figcaption></figure>

The next mode is the subtract mode, this mode does the opposite of the extend mode we just went over.

**Select Linked**

With the shortcut `Ctrl+L`, Blender will select everything up to a certain boundary. By default, this boundary is the same piece of 3d geometry, but in the bottom left corner of the viewport, you can pick the delimiter:



<figure><img src="../../../.gitbook/assets/blender_select_linked.png" alt="" width="213"><figcaption></figcaption></figure>

See [#seams-and-sharps](./#seams-and-sharps "mention") how to make use of this!

#### Select Loops

Hold `Alt` and left click to instantly select an entire loop of vertices, edges, or faces.&#x20;

{% hint style="info" %}
This doesn't work well with geometries that are **complex** or **triangulated** (Cyberpunk meshes are usually at least one of these things). You can [un-triangulate](https://blender.stackexchange.com/questions/13727/how-do-you-un-triangulate-a-mesh) a mesh for easier loop selection (hotkey: `Alt+J`), then re-triangulate it again before exporting (Hotkey: `Ctrl+T`)
{% endhint %}

#### Select Boundary loops

Select all or part of a mesh then navigate to :

<figure><img src="../../../.gitbook/assets/Screenshot 2024-05-20 111519.png" alt=""><figcaption></figcaption></figure>

this will instantly select all boundary loops for the given selection, great for marking seams

#### **Select shortest path**

Works in Edge, Vertex, or Face Selection Mode. Select at least one element, then `Ctrl+click` on **any other element** to select the shortest path of edges, vertices, or faces between them.&#x20;

{% hint style="info" %}
Double-check that the shortest path is actually the path you want. If it's not, **un-do** (Hotkey: `Ctrl+Z`) and shift-click on an edge closer to your selection.
{% endhint %}

### Seams and Sharps

In Edge Selection Mode (Hotkey: `2`), you can (un)mark **edges** as **seams** or **sharps** via context menu:

<figure><img src="../../../.gitbook/assets/blender_ui_guide_3_seams_and_sharps.png" alt=""><figcaption><p>Seams are orange, Sharps are blue</p></figcaption></figure>

A **seam** (orange line in the viewport) is where the UV map will be split.&#x20;

{% hint style="info" %}
A [full explanation on UV mapping](../../materials/uv-mapping-texturing-a-3d-object.md) blows the scope of this guide, but you can read on if you're curious.

**Unless you're UV unwrapping**, those won't do anything, and you can use them as selection delimiters to your heart's content!
{% endhint %}

A sharp (blue line in the viewport) **will cause a sharp crease/fold** in the material. This translates to Cyberpunk, so it's neat to highlight your edges!

### Proportional Editing

{% hint style="success" %}
You can find a detailed guide on this under [r-and-r-refitting-step-by-step.md](../../../modding-guides/items-equipment/recolours-and-refits/r-and-r-refitting-step-by-step.md "mention") -> [#step-4-refitting](../../../modding-guides/items-equipment/recolours-and-refits/r-and-r-refitting-step-by-step.md#step-4-refitting "mention")
{% endhint %}

"I'm moving a single vertex, but my entire mesh is affected!"&#x20;

Sounds familiar? You've run into Proportional Editing.

<figure><img src="../../../.gitbook/assets/blender_proportional_editing.png" alt=""><figcaption></figcaption></figure>

* Click the button or press `O` to turn it off and on
* When it's active, **moving**, **scaling** or **rotating** will have an effect on anything **close to your selection**. This makes refitting super easy! No more jagged edges!
* When you move (`G`) or scale (`S`) your selection, you will see a circle for the area of  its effect.&#x20;
  * By default, that circle might be huge and outside your screen. You might wanna change this and then [#save-startup-file](./#save-startup-file "mention").
  * You can change the circle's size with your mouse wheel

### Face Orientation

&#x20;Each mesh has an inside and an outside. Most materials don't even show the inside, so it's kinda important to know which is which.

Once you have entered Edit Mode, you can show Face Orientation from the menu at the top right of your viewport:

<figure><img src="../../../.gitbook/assets/blender_for_beginners_show_normals.png" alt=""><figcaption><p>Image credit: <a href="https://3dmodels.org/blog/how-to-fix-normals-in-blender/">3dmodels.com</a></p></figcaption></figure>

To turn a face inside out, you can use the Normals menu (Shortcut: `Alt+N`) and select **Flip**:

<figure><img src="../../../.gitbook/assets/blender_for_beginners_flip_normals.png" alt=""><figcaption></figcaption></figure>

#### Flipped faces

Sometimes, faces are messed up. To find faces with flipped normals, go into Edge Selection Mode (Hotkey: `2`) and use **Select -> Select Sharp Edges:**

<figure><img src="../../../.gitbook/assets/blender_for_beginners_s-arp_edges.png" alt=""><figcaption></figcaption></figure>

## The Scripting perspective

Blender offers a fully-fledged Python environment, which is used by **Netrunners** to develop **plugins** like the [wolvenkit-blender-io-suite](../../modding-tools/wolvenkit-blender-io-suite/ "mention").&#x20;

Since you are reading this, you're probably not one of those. Don't worry! Some of our guides tell you to run Python scripts, but we have a dedicated guide for that: [blender-running-python-scripts.md](blender-running-python-scripts.md "mention")

[^1]: A "point" between two Edges and the corner of a Face

[^2]: The connecting line between two vertices and the boundary of a Face

[^3]: A plane. Its sides are Edges, its corners are Vertices.
