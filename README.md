# Avatar assets and templates for Mozilla Hubs

This contains some useful working files for editing avatars for [Mozilla Hubs](https://hubs.mozilla.com). 

**IMPORTANT:  If you are cloning this repo, _you MUST first install [GitLFS](https://git-lfs.github.com/)_ or else many of the files will not work.**

Depending on how involved you'd like to get in the avatar creation process, you might choose to simply 're-skin' the existing robot avatar by painting your own texture maps, or create your own fully custom 3D model.

## Making your own custom avatar skin

A quick and easy way to create a custom avatar in Hubs is to create a custom skin using an image editor or texturing tool. We have a [Getting Started Tutorial](https://docs.google.com/document/d/1K1Eos1sjqN4N9lPlYQfvU53v8f1HxmdTZRjH4RLrGq8/edit) to help you create your first avatar skin.

You can use the following resources:

* [Quilt](https://tryquilt.io/) - A simple tool put together by the Hubs team for quickly re-skinning the default Hubs robot avatar. 

* [Photoshop PSD Templates](Photoshop) - Photoshop templates for a custom Hubs base color skin. You can also use Photoshop's 3D painting tools, using the [Robot OBJ/MAT file](https://github.com/j-conrad/hubs-avatar-pipelines/tree/master/Other%20model%20formats).

* [Substaince Painter Project](Substance) - Full [Substance Painter](https://www.allegorithmic.com/products/substance-painter) projects for advanced custom skinning. You can also download and modify any of our [example texture sets](Exported%20Texture%20Sets).

![UV Layout example](docs/UVLayout.jpg)

The UV layout for the base robot avatar is purposefully symmetrical along the X (horizontal) axis. This makes it relatively easy to paint one half of the texture(s) and flip it to the other side. Some image editing applications such as Photoshop have built-in mirroring tools that allow you to paint both halves in real time.

![Panda Bot example](docs/PandaBot.jpg)

The simplest version of re-skinning the robot avatar would be to simply paint a 'baseColor' map. However, because Hubs uses glTF standards it supports many of the map types associated with [physically-based materials](https://www.allegorithmic.com/pbr-guide). 
The default avatar is currently using:
- Base Color
- Emissive
- Normal
- Ambient Occlusion
- Roughness (black = glossy, white = rough)
- Metallic  (black = non-metal, white = fully metallic)

**NOTE: Ambient Occlusion, Roughness, and Metallic must be combined in one singular image with each texture occupying the Red, Green, and Blue channels respectively.** This is sometimes referred to as an _'ORM'_ texture.

**It is _highly_ recommended that texture resolution be kept at 1024x1024 or below.** This is mostly due to Hubs being a web-based application where large download times for bigger files can hurt performance, especially on mobile devices. _All textures MUST be powers of 2 (64, 128, 256, 512, etc.)_

## Making your own custom avatar model

We offer the following resources if you'd like to modify our Robot avatar:

* [Blender Source Files](Blender/AvatarBot) are available of our Robot avatar. **For specific information about how to use these .blend files, be sure to check out the readme within the [Blender/AvatarBot](/Blender/AvatarBot) folder.**

* [Exported GLBs](Exported%20GLB%20models)/[Exported OBJ](Other%20model%20formats)  are available if you'd like to bring them into your editor of choice.

We recommend using [Blender 2.8 beta](https://builder.blender.org/download/) for custom models since we have provided example files that you may use as a guide. (Typically, skeleton setup varies between modeling appications which can make importing/exporting skeletons a bit tricky due to unexpected changes in bone rotations, but it is still possible to use something other than Blender.) Note: the .blend files were created with [Blender 2.8 beta](https://builder.blender.org/download/) due to the built-in glTF exporter. The glTF importer/exporter for Blender is currently in development. Expect some bugs and [please report them!](https://github.com/KhronosGroup/glTF-Blender-IO/issues)

Hubs avatars are meant for VR, which means that you should work in real world units. A typical avatar height is roughly 1.7 meters. Note: This is typically a 'standing height'. The lack of legs shown here is a part of that overall height.

![avatar height diagram](docs/avatarHeight.jpg)

Files with the suffix *_base* refer to the most barebones, basic robot avatar template that can be used as a reference when creating new avatar models. Typically, the Blender workflow would be to either 'Link' or 'Append' the objects from [AvatarBot_base_for_export.blend](/Blender/AvatarBot) in order to use the existing armature (skeleton) and any animations that go along with it, using them as a basis for your own model that you would attach to it.

The armature is based largely upon the same hierarchy and naming conventions of the skeleton provided by [High Fidelity](https://docs.highfidelity.com/en/rc80/create/avatars/avatar-standards.html#skeleton). This also happens to have a similar structure to VRChat in terms of bone orientations.
However, in our current implementation in Hubs, we have eliminated some of the bones within the hierarchy, namely the lower body and arm joints since we are not using any sort of inverse kinematics (IK) at the moment. This may change in future iterations.

# License

All assets are licensed with the [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

Code is licensed with the [Mozilla Public License 2.0](https://www.mozilla.org/en-US/MPL/).
