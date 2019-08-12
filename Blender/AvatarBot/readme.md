# Blender files for AvatarBot

## AvatarBot_base_for_export.blend

**This is a Blender 2.8 file.**

**This is the most important file used when exporting to a final glTF or glb.**

It is the base (default) robot avatar used by Hubs and can be useful to dissect how Hubs avatars work or when attempting to make your own.

**AvatarBot_base_for_export_altbody.blend** is identical except that it has a lattice deformer modifier on it that adjusts the shape of the body to be more of an 'hourglass' silhouette. You can adjust that lattice to experiment with different body shapes. This ensures that the UV layout does not change and you can use the same textures for any new shaped body you make.

## Skeleton and animation

The file contains a model rigged with an skeleton (Armature). The armature may be hidden when opening the file in Blender. You can unhide it via the 'Object Types Visibility' dropdown in the 3d viewport. 

![Object Types Visibility menu](/docs/BlenderArmatureVisibility.jpg)

The model's vertices are all weighted either zero or 100% to a bone. This is not a hard requirement for Hubs avatars, just a choice made for this particular avatar design. The process of adding another mesh (like a hat) to this avatar would involve 'Joining' your new mesh to this model, then in Edit Mode, assigning its vertices to the corresponding Vertex Group, such as the head.

![Vertex Groups in Blender](/docs/VertexGroups.JPG)

Hubs avatars do not currently employ any sort of IK (Inverse Kinematics) for elbows or feet. This may change in future iterations.

The skeleton has been animated with several important short clips (Actions), namely all the various finger positions for when it is controlled via 6DOF controllers like on the Oculus Rift/Quest or the HTC Vive.
There is also an animation that makes the robot's eyes move around a bit to give it a little more life, but this is manually set to loop in the glTF file itself.


![Animation Actions in Blender](/docs/AnimationActions.JPG)

There are some unused shape keys (morphing) on the model, such as eye blinking and mouth shapes. In the future, some of these may get used as this avatar workflow develops but for now, you can safely ignore or delete them when making your own model.

In Hubs, you may notice that the robot's head scales up when someone talks via their microphone. This is driven by having a `scale-audio-feedback` component on the head node in the glTF, and is not hard-coded. Future iterations may make use of mouth shapes or other movements.

## Materials 

The model has a BSDF material applied to it which is set up as per the [glTF 2.0 guidelines within the Blender 2.8 manual](https://docs.blender.org/manual/en/dev/addons/io_gltf2.html). Some of this setup may be changing as the glTF specifications get updated so it is recommended to check back on that documentation periodically.
Because the importer/exporter add-on is updated more frequently than Blender 2.8, it is recommended that you update and install that add-on manually.

The default textures on the model are located in the [Exported Texture Sets](../Exported%20Texture%20Sets/_Bot_Base) folder in this repo. If you are not creating entirely new maps, you must download the textures and place them in their corresponding nodes in the Blender shader window in order to export the model successfully. 

## Exporting

When exporting to use in Hubs, most of the default settings for the glTF exporter will be fine the way they are. The one exception is to turn *'Apply Modifiers' _ON_*. This ensures that the model gets exported with proper smoothing groups. This is currently a non-ideal situation and is part of why using shape keys does not fully work yet. (Stay tuned to glTF exporter improvements that will fix this problem.)

## Other .blend files

The other files here are examples of low/high polygon meshes that were used in the process of baking normal maps within Substance Painter.
For the most part, you can ignore these files, but they are left here for demonstration purposes.
