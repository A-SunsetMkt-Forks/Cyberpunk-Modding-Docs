---
description: How to make it iconic
---

# Adding stats, modifiers, and mod slots

## Summary

**Published:** Jan 29 2024 by [manavortex](https://app.gitbook.com/u/NfZBoxGegfUqB33J9HXuCs6PVaC3 "mention")\
**Last documented update:** May 04 2024 by [manavortex](https://app.gitbook.com/u/NfZBoxGegfUqB33J9HXuCs6PVaC3 "mention")

This guide will show you an example for adding a modifier to an existing game item; in this case, making David's jacket iconic.&#x20;

It will point you towards further reading material in case you want to dig deeper.

## How to mod it

Find [the-cyberpunk-2077-game-directory](../../../../for-mod-users/users-modding-cyberpunk-2077/the-cyberpunk-2077-game-directory/ "mention"). Then, create the following **text document** (you can name it what you want):

```
r6/tweaks/my_improved_item.yaml
```

Paste the following contents into the text document and save it:

```yaml
Items.MQ049_martinez_jacket:
  statModifiers:
    - !append Quality.IconicItem
```

That's it. When you start the game now, the item's quality will be iconic.

### What the fuck did I just do?

You created a tweak edit.

## Removing properties

If you want to **safely delete** a record property, set its value to **None**. For example:

```yaml
Items.MQ049_martinez_jacket:
  displayName: None
```

You might not want to actually do it.

## Adding attachment slots

To add **attachment slots** to an item, you would need to change its **blueprint** property by either using other blueprints or create a new one using this guide&#x20;

{% content-ref url="../../../../for-mod-creators-theory/core-mods-explained/tweakxl/tweakxl-changing-game-records/creating-custom-blueprints.md" %}
[creating-custom-blueprints.md](../../../../for-mod-creators-theory/core-mods-explained/tweakxl/tweakxl-changing-game-records/creating-custom-blueprints.md)
{% endcontent-ref %}
