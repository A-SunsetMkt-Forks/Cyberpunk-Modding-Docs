# CCXL: Hairs

## Summary

Published: Jan 20 2025 by [mana vortex](https://app.gitbook.com/u/NfZBoxGegfUqB33J9HXuCs6PVaC3 "mention") and [IslandDancer](https://app.gitbook.com/u/s8gktWvqEZWGRxQIsePwOnEI2Mo2 "mention")\
Last documented edit: July 14 2025 by [nutboy](https://app.gitbook.com/u/y772Qw4Ul9cmqXiuTKkTpLxDVzQ2 "mention"), [mana vortex](https://app.gitbook.com/u/NfZBoxGegfUqB33J9HXuCs6PVaC3 "mention"), [IslandDancer](https://app.gitbook.com/u/s8gktWvqEZWGRxQIsePwOnEI2Mo2 "mention"), [CyberVesna](https://app.gitbook.com/u/cmjyzwfGm7YaRhuU9Kyk4uTuE3Y2 "mention")  and [Silverlags](https://app.gitbook.com/u/3GmqMieZ5BZ87uRqI3Y1Uj7tEHy1 "mention")

This page will tell you how to use ArchiveXL to add hair to the character creator.&#x20;

### Wait, this is not what I want!

* To learn more about the character creator, check [files-and-what-they-do](../../../files-and-what-they-do/ "mention") -> [character-creator](../../../files-and-what-they-do/file-formats/character-creator/ "mention")
* To convert an existing hair mod to CCXL, check [convert-a-hair-mod-to-hair-ccxl-mod.md](../../../../modding-guides/npcs/guides-all-about-hair/convert-a-hair-mod-to-hair-ccxl-mod.md "mention")

## Requirements

You have downloaded the example project from [Nexus](https://www.nexusmods.com/cyberpunk2077/mods/19228)

## TL;DR

If you would rather understand what you're doing, please skip to [#step-1-deleting-.ent-files](ccxl-hairs.md#step-1-deleting-.ent-files "mention")!

1. Download example project
2. Add your `.mesh` file to the project
3. Copy the `appearances`, `materialEntries`, and `localMaterialDefinitions` from the template mesh
4. Overwrite it with your own
5. Overwrite the `.rig` and the `.animgraph` with your own, if you have them
6. Adjust `.app` file entry
7. If you're not using base game textures: Change files paths in the `.mi`
8. Rename the `.xl` file
9. Change translation key in the `.json` file to something unique for your mod
10. Change translation entries in the `.inkcharactercustomization` file
11. Custompath everything — do not publish anything that still contains tutorial files!
12. Profit

## Let's go!

We will be moving **backwards** through the files: starting at the bottom, and working our way to the top (the character creation and the .xl control file).

1. Start by downloading the example project from [Nexus](https://www.nexusmods.com/cyberpunk2077/mods/19228)
2. Unpack the `source` folder into the root of your existing hair project so that it merges with yours
3. Move any `.mesh`, `.animgraph`, and `.rig` files from your original hair to `your_modder_name\ccxl\your_first_addition\meshes`&#x20;

## Step 0: Deleting empty meshes

Starting with 8.16.2, Wolvenkit has the menu option `Project` -> `Clean up` -> `Delete empty meshes`. This will delete placeholder files from your hair mod.

## Step 1: Deleting .ent files

If you don't have any `.ent` files, you're good!&#x20;

If you do have them, delete them now – we don't need them in our CCXL projects.

## Step 2: Adjusting the .app file

<details>

<summary>If you are converting an existing mod with an .app file</summary>

It is often easier to convert the existing file and replace the template mod's `.app` with it, especially when you are using more than one hair mesh.

1. **Delete** all but the first appearance.

1) `partsValues`  are unused and should be left blank.
2) `partsOverrides` are not used by hairstyles in the basegame, but ArchiveXL does use them to generate/expand appearances in .app and to unambiguously resolve `meshAppearance` per component per `appearanceAppearanceDefinition`.
3) ArchiveXL has fallback behavior in the event `partsOverrides` are missing. It will try to recognize which components are meshes that require `meshAppearance` to be set, but it it can make incorrect assumptions in complex cases involving many components. Best practice is therefore to add `componentOverrides` and set `componentName` and `meshAppearance` but leave `depotPaths` blank.

</details>

### Your .app should look like this:

<figure><img src="../../../../.gitbook/assets/ccxl_mesh_file_02 (1).png" alt=""><figcaption></figcaption></figure>

## Your .app partsOverrides should look like this:

<figure><img src="../../../../.gitbook/assets/image (618).png" alt=""><figcaption></figcaption></figure>

## Wait, I'm missing meshes!

If you have more than one .mesh file, for every additional mesh, complete the following steps:&#x20;

1. Duplicate the `entAnimatedComponent`&#x20;
   1. Change the `rig` 's depot path to the relative path of the corresponding .rig file
   2. Change the `graph's` depot path to relative path of the corresponding .animgraph file
   3. Change the `name` so that it's unique (add `_pt_1` at the end or number it)
2. Duplicate the `entSkinnedMeshComponent` &#x20;
   1. change the depot path to point it at your extra mesh
   2. Select `parentTransform` and change the `bindName` to your `entAnimatedComponent`'s name (step 1c above)
   3. Select `skinning` and change the `bindName` to your `entAnimatedComponent`'s name (step 1c above)
   4. Change the `name` to be unique
3. Duplicate the `appearancePartComponentOverrides` in `partsOverrides`
   1. change the `componentName` to your new `entSkinnedMeshComponent` 's name from step 2
   2. repeat this step for each new meshComponent you add
4. Optional: Component uniqueness
   1. If you are running into issues, you can assign unique `id`s to all of your components. Go through them one by one, select their `id` attribute, and select "`Generate new CRUID`" from the context menu.

### How does this work?

Thanks to ArchiveXL magic, your .app file needs **only one appearance**. All other appearances will be extrapolated from it!

You can use any of the existing base game hair colours, as long as the definition itself is valid.

The template file has three `.app` files – one of them is for your hair's default appearance, one is for the `cyberware_01` appearance, and one is for the first person hair.&#x20;

If you do not have a cyberware\_01 appearance, you can **delete** this file and adjust the file path under [#step-6-the-.incharactercustomization-file](ccxl-hairs.md#step-6-the-.incharactercustomization-file "mention")

{% hint style="info" %}
If you want to add more meshes/rigs to the template .app (for example from uuhv4), you can **duplicate** the `entSkinnedMeshComponent` and the matching `entAnimatedComponent` from the context menu.
{% endhint %}

{% hint style="info" %}
File Validation can help you making sure that your hair components and paths are correct.&#x20;
{% endhint %}

## Step 3: The .mesh files

This section will explain how ArchiveXL works its magic to pick all the right hair colours and -textures from three entries and a piece of duct tape.

{% hint style="info" %}
If you are converting an existing hair mod, you probably already have these files.&#x20;

In this case, copy `appearances`, `materialEntries`, and `localMaterialInstances` from the template file to your existing hair mesh.&#x20;
{% endhint %}

We'll now go through everything step by step.

### 3.1 Appearances

{% hint style="info" %}
To understand appearances, you can check [3d-objects-.mesh-files](../../../files-and-what-they-do/file-formats/3d-objects-.mesh-files/ "mention")-> [#step-1-appearances](../../../files-and-what-they-do/file-formats/3d-objects-.mesh-files/#step-1-appearances "mention"). This is not necessary to complete the guide, though!
{% endhint %}

As you can see, you only need a single appearance — ArchiveXL will generate all the rest.&#x20;

{% hint style="warning" %}
If your hair mesh is set up differently from the template file, you need to adjust the chunk materials here!
{% endhint %}

<figure><img src="../../../../.gitbook/assets/ccxl_mesh_file_01.png" alt=""><figcaption></figcaption></figure>

In our example, the first submesh uses the material `@long`, and the second one the material `@cap`. &#x20;

The names must be set as follows:

```
<name_of_appearance>@<name_of_material> => black_carbon@long
```

### 3.2 Material definitions

{% hint style="info" %}
To understand material definitions, you can check [3d-objects-.mesh-files](../../../files-and-what-they-do/file-formats/3d-objects-.mesh-files/ "mention") -> [#step-2-material-registry](../../../files-and-what-they-do/file-formats/3d-objects-.mesh-files/#step-2-material-registry "mention"). This is not necessary to complete the guide, though!
{% endhint %}

The tutorial hair has only two materials, and three material entries (`@context`, `@long`, `@cap`):

<figure><img src="../../../../.gitbook/assets/ccxl_mesh_file_02.png" alt=""><figcaption></figcaption></figure>

You can define more materials here if you need them (please note the box below)

{% hint style="warning" %}
You have to use the exact material names that ArchiveXL is expecting, or extra hair colours won't work.

For a full list, see [.](./ "mention") -> [#hair-materials](./#hair-materials "mention")
{% endhint %}

Now, let's look at the materials themselves.

### 3.3 Materials

You have to repeat this step for every mesh file in your project. Be careful, as different meshes may use different texture sets. In this case, you need an extra `.mi` file for them.

{% hint style="info" %}
To understand materials, you can check [3d-objects-.mesh-files](../../../files-and-what-they-do/file-formats/3d-objects-.mesh-files/ "mention") -> [#step-3-material-definition](../../../files-and-what-they-do/file-formats/3d-objects-.mesh-files/#step-3-material-definition "mention"). This is not necessary to complete the guide, though!
{% endhint %}

{% hint style="info" %}
You can read more about @context and appearance extrapolation under [#material-colour-extensions](ccxl-theory-scopes-and-extensions.md#material-colour-extensions "mention"). This is not necessary to complete the guide, though.
{% endhint %}

#### @context&#x20;

This is a blank container for storing contextual parameters. This is not a functioning material instance.

You can use contextual parameters in any mesh by creating a blank material named `@context` .&#x20;

Please note the following:

* It should always be the first `materialEntries`. That is, it should always be index position 0.
* `baseMaterial` should always be _null_.
* In `values` you then create a key whose value is a string of type `CpuNameU64`.&#x20;
* If you wish to use basegame materials as is, this string may be any context BaseMaterial in PlayerCustomizationHairFix.xl. e.g.:

```yaml
  context:
    LongBaseMaterial: base\characters\common\hair\textures\hair_profiles\_master__long_bright.mi
    CapBaseMaterial: archive_xl\characters\common\hair\textures\hair_profiles\hh_025_ma__pompadour_cap.mi
```

* You can find all of the fix xl configs in "Cyberpunk 2077\red4ext\plugins\ArchiveXL\Bundle\\". Do not modify these files in any way, as they are required for CCXL hair implemention to function correctly. &#x20;
* If you wish to change basegame materials (e.g. path to custom hair textures), then your @context string will be a path to one of the external material instance ( `.mi` ) files in the project.
* You can create a contextual parameter by doing the following:

<figure><img src="../../../../.gitbook/assets/ccxl_mesh_file_04.png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
You need to create **one** entry for every type of material that you want ArchiveXL to expand.

For a full list, see [ccxl-theory-scopes-and-extensions.md](ccxl-theory-scopes-and-extensions.md "mention")-> [#hair-materials](ccxl-theory-scopes-and-extensions.md#hair-materials "mention")
{% endhint %}

{% hint style="warning" %}
If your hair is using a material multiple times (e.g. long, long, cap), you still create **only one** LongBaseMaterial value.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/ccxl_mesh_material_context.png" alt=""><figcaption></figcaption></figure>

#### @long&#x20;

This material defines the hair cards. It points at the `.mi` file in your project, where the hair's textures are defined.

{% hint style="warning" %}
All ResourcePaths must have `Soft` flags for this to work, including the `baseMaterial`! (see screenshot)
{% endhint %}

Since the dynamic context does not transfer to the `.mi`, we need to set the `HairProfile` here.&#x20;

The `{material}` placeholder in the file entry will be replaced with the chunk mask name from the appearance (e.g. `black_carbon`).

<figure><img src="../../../../.gitbook/assets/ccxl_mesh_file_05.png" alt=""><figcaption></figcaption></figure>

#### @cap&#x20;

This material defines the hair cap (the stubbles on the scalp). It points at the `.mi` file in your project, where the scalp's textures are defined.

<figure><img src="../../../../.gitbook/assets/ccxl_mesh_file_06.png" alt=""><figcaption></figcaption></figure>

Since the dynamic context does not transfer to the `.mi`, we need to set the `GradientMap` here.  Omitting this will lead to the hair cap looking way darker than it's supposed to.

## Step 4: The .mi files

{% hint style="info" %}
The `.mi` file and the `@context` are required for ArchiveXL character creator extensions. Without a .mi file, you won't have e.g. extra hair colours (e.g. [Hair Profiles CCXL](https://www.nexusmods.com/cyberpunk2077/mods/19115))
{% endhint %}

With the exception of the hair cap, the .mi file is a completely normal [material tempate file](../../../files-and-what-they-do/file-formats/materials/re-using-materials-.mi.md) (link not necessary for understanding this guide).&#x20;

The hair cap base material is included within ArchiveXL. If you aren't using one, you don't need to know any of this — just move all properties without dynamic properties from the `.mesh` file into your `.mi`.

<figure><img src="../../../../.gitbook/assets/ccxl_mi_file.png" alt=""><figcaption></figcaption></figure>

## Step 5: The translation entry

Open the included .json file, and make sure to change the entries according to your needs.

There are two translation entries, because this tutorial assumes that you want to name the `cyberware_01` variant differently.&#x20;

For an explanation of what is what, keep reading.

<figure><img src="../../../../.gitbook/assets/ccxl_json_01.png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="187">key</th><th width="238.5">value</th><th>explanation</th></tr></thead><tbody><tr><td><code>femaleVariant</code></td><td><code>Your First Hair</code></td><td></td></tr><tr><td><code>maleVariant</code></td><td><em>leave it blank</em></td><td>If no value is found, then <code>femaleVariant</code> acts as default</td></tr><tr><td><code>primaryKey</code></td><td>0</td><td>Will be generated by ArchiveXL, leave it alone</td></tr><tr><td><code>secondaryKey</code></td><td><code>UI-Customization-your_first_hair</code></td><td>Used in the <code>.inkcharactercustomization</code> file to set your hair's entry name</td></tr></tbody></table>

## Step 6: The .`inkcharactercustomization` file

Here is where everything connects to each other.&#x20;

{% hint style="info" %}
For more information about this, see [.inkcharactercustomization-cc-options.md](../../../files-and-what-they-do/file-formats/character-creator/.inkcharactercustomization-cc-options.md "mention")
{% endhint %}

Open the file, we will look at the entries now.

### 6.1 headGroups

These entries **create** character creator additions, while the CustomizationOptions **define** them (think of a materialDefinition and a materialInstance in a `.mesh` file).

<figure><img src="../../../../.gitbook/assets/ccxl_inkcc_headgroups.png" alt=""><figcaption></figcaption></figure>

### 6.2 gameUiSwitcherInfos

Let's take a look at the `headCustomizationOptions`. The first to entries of the type `gameuiSwitcherInfo` add our new hair to Cyberpunk's character creator menu, so that they show up when you scroll through the hairs.

#### The first entry

{% hint style="danger" %}
If you're only using one hairstyle mesh, keep this entry nameless, or it will overwrite the [character-creator](../../../files-and-what-they-do/file-formats/character-creator/ "mention")'s base [switcher](../../../files-and-what-they-do/file-formats/character-creator/#the-switcher)!
{% endhint %}

* **link**: Targets one of the `headGroups` entries
* **names**: Contains the `headGroup`'s `options`

<figure><img src="../../../../.gitbook/assets/ccxl_inkcc_2.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
If you want to use a different mesh when cyberware\_01 is enabled, you will have to cut "hairstyle" from the `link` in the first entry and instead put it in `name` to have two visibly distinct meshes. Otherwise you'll only have one mesh visible.
{% endhint %}

#### The second entry: `hairstyle_cyberware`

This entry defines the hairstyle for `cyberware_01`. &#x20;

### 6.3 `gameUiAppearanceInfo`s

{% hint style="info" %}
For more information on this, see [.inkcharactercustomization-cc-options.md](../../../files-and-what-they-do/file-formats/character-creator/.inkcharactercustomization-cc-options.md "mention") -> [#gameuiappearanceinfo](../../../files-and-what-they-do/file-formats/character-creator/.inkcharactercustomization-cc-options.md#gameuiappearanceinfo "mention"). This is not necessary for the purpose of this guide!
{% endhint %}

The template inkcc has three `gameUiAppearanceInfo`s, one for your hair, one for the cyberware\_01 variant, and one for FPP.

If you do not have an extra appearance for cyberware\_01, you can re-use the default hair `.app` file.

Make sure to adjust the paths to your corresponding .app file:

<figure><img src="../../../../.gitbook/assets/ccxl_inkccfile_1.png" alt=""><figcaption></figcaption></figure>

## Step 7: The .xl file

From your project's resource directory, open the `.archive.xl` file that you created in the previous guide. Add the following lines at the bottom (make sure that there are no leading spaces):

```yaml
customizations:
  female: your_modder_name\ccxl\your_first_addition\_pwa.inkcharcustomization
localization:
  onscreens:
    en-us: your_modder_name\ccxl\your_first_addition\localization\your_first_hair_wa__local.json
resource:
  scope:
    player_wa_hair.app:
      - your_modder_name\ccxl\your_first_addition\appearances\your_first_hair_wa.app
      - your_modder_name\ccxl\your_first_addition\appearances\your_first_hair_wa_cyberware.app
      - your_modder_name\ccxl\your_first_addition\appearances\fpp\your_first_hair_wa_fpp.app
    player_wa_hair.mesh:
      - your_modder_name\ccxl\your_first_addition\meshes\your_first_hair_wa.mesh
      - your_modder_name\ccxl\your_first_addition\meshes\your_first_hair_wa_cyberware.mesh
```

<details>

<summary>TODO: What does this do?</summary>

It just works. Adjust the paths!

</details>



## Step 8: Renaming and moving

Now it's time to [custompath](../../../../modding-guides/items-equipment/custompathing-assets.md) your project.&#x20;

<figure><img src="../../../../.gitbook/assets/ccxl_custompathing.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
On some versions of WolvenKit, you might encounter an issue where a file like `.inkcharcustomization`  fails to apply the custom path, in that case you'll have to open the file and copy relative path of your `.apps`&#x20;

It's recommended to look in the Log view and check if there's an error in a renaming custompaths in files.&#x20;
{% endhint %}

## Troubleshooting

### Hair colour extensions don't work on my hair!

Most likely, you screwed up the names of your material definitions. They must be **exactly** as ArchiveXL expects them to be.\
Go back to [#id-3.2-material-definitions](ccxl-hairs.md#id-3.2-material-definitions "mention") and double-check everything.

Otherwise, check that your `componentsOverride` in the `partsOverrides` of the `.app` is correctly named. (see [#your-.app-partsoverrides-should-look-like-this](ccxl-hairs.md#your-.app-partsoverrides-should-look-like-this "mention"))

If that doesn't help, check the log (see [#my-hair-is-always-black](ccxl-hairs.md#my-hair-is-always-black "mention"))

### My hair is always black!

That happens when the material patching/expansion didn't work. \
Search the [ArchiveXL log](../../../../for-mod-users/user-guide-troubleshooting/finding-and-reading-log-files.md#a-list-of-framework-logfiles) for the name of the broken hair mesh. Most likely, there is a warning or an error that you can fix.

### I have duplicate entry in hairstyles options!

This happens due to having a different `localizedName` for`cyberware_hairstyle` switcher that's inside the`.inkcc` file. For example`UI-Customization-your_first_hair` in the blank switcher, and `UI-Customization-your_first_hair_cyberware`  in the `cyberware_hairstyle` switcher.&#x20;

If you want to have a unique hairstyle mesh when cyberware\_01 is enabled refer to [#id-6.2-gameuiswitcherinfos](ccxl-hairs.md#id-6.2-gameuiswitcherinfos "mention"), specifically the hint about `link` and `name`.
