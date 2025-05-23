---
description: 'How everything is connected, or: why your edited mesh moves weirdly'
---

# Meshes and Armatures: Rigging



## Summary

This page will give you a short explanation on why 3d objects are moving.

### Wait, this is not what I want!

* To learn what a rig even is, check [armatures-.rig-files.md](../../files-and-what-they-do/file-formats/armatures-.rig-files.md "mention")
* Maybe you want the [weight-painting-for-gonks.md](weight-painting-for-gonks.md "mention") guide?
* For a documentation of the import/export options in Wolvenkit, check [here](https://wiki.redmodding.org/wolvenkit/wolvenkit-app/editor/import-export/models#choosing-rigs-correctly).&#x20;
* Guides on how to transfer weights between rigs: [blender plugin](../../modding-tools/wolvenkit-blender-io-suite/#transfer-vertex-weights), [youtube video](https://www.youtube.com/watch?v=bR_Vke__voU), [wiki page](../../../modding-guides/npcs/custom-facial-piercings-prc-framework.md#weight-painting)&#x20;

The connection between a mesh and a rig is made via **vertex groups**. Any number of vertices can be assigned to a group, which is then matched to a rig's bone via **name**.

<figure><img src="../../../.gitbook/assets/rigging_meshes_vertex_groups.png" alt=""><figcaption><p>These vertices move with the bone "Spine3"</p></figcaption></figure>

How much every bone influences the vertices is determined by vertex weight, which can be altered in Blender's Weight Paint perspective:

<figure><img src="../../../.gitbook/assets/rigging_meshes_vertex_weights.png" alt=""><figcaption><p>Weight painting</p></figcaption></figure>

Vertex weights are assigned for every vertex group, and each vertex will move on the basis of the sum of all its weights.&#x20;

{% hint style="success" %}
To preview the deform in Blender, you can select the mesh's parent armature and enter the "Pose Mode". There, you can either apply an [exported animation](https://wiki.redmodding.org/wolvenkit/guides/modding-community/exporting-to-blender/exporting-rigs-and-anims), or select individual bones and rotate/move them. The **Armature modifier** will morph your mesh according to the pose, letting you spot errors much faster than trying to debug them in-game.
{% endhint %}

{% hint style="info" %}
You can see a video of the process [here](../../../modding-guides/npcs/) (courtesy of Vesna).&#x20;
{% endhint %}
