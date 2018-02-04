# Models

![Models](media/title.png)

**Models** are one of the most important parts of the games. Player character and whole environment can be created using them. Flax supports importing model files created by using the most common 3D modeling software (e.g. Maya, 3dsMax, Blender) or generating procedural geometry.

A Model asset contains a collection of **Level Of Details** (shorten as *LOD*) and **Material Slots**. Each LOD contains a collection meshes to draw. During model rendering, each mesh uses a specific material slot which can hold the default value or be overridden by the [Model Actor](model-actor.md).

![Model Design](media/ModelDesign.png)

> [!Note]
> The maximum amount of levels of details for the model is `6`. Also, each LOD can contain up to `4096` meshes.

A **mesh** consists of triangles arranged in 3D space to create the impression of a solid object. A triangle is defined by its three corner points (called vertices). In the [Mesh](http://docs.flaxengine.com/api/FlaxEngine.Mesh.html) class, the vertices are all stored in a single array and each triangle is specified using three integers that correspond to indices of the vertex array. The triangles are also collected together into a single array of integers; the integers are taken in groups of three from the start of this array, so elements 0, 1 and 2 define the first triangle, 3, 4 and 5 define the second, and so on. Any given vertex can be reused in as many triangles as desired.

## Model LOD switching

Flax supports dynamic model LODs switching based on a model instance screen size (in percentage). Here is an example of this feature:

![Model LOD switching](media/model_lods_switching.gif)

## Importing models

To learn about importing model assets and adjusting import settings read the dedicated [page here](import.md).

## Using models

Model assets are used by the many parts of the engine. The most common case is by creating a **Model Actor**. That actor type renders a model and allows to override some of its properties like shadows casting or material slots collection. To learn more about it see a dedicated [page here](model-actor.md).

## Procedural geometry

Flax provides a C# scripting API to generate procedural mesh geometry offline or at runtime.
Created model from code can have all the proeprties as the imported one. Althog there are some limitations like no baking lightmaps or reduced amount of LODs. Hovewer procedural models can be saved to the asset file in the editor and then used in a game. This feature can be highly used by the Editor Plugins.

To learn more about creating procedural meshes see the [tutorial here](generate-model.md).

## Vertex properties

Flax uses fixed model data format. Although index buffer can use 16 or 32-bit format layout vertex buffers layout is strictly defined. Vertex Buffers data is highly compressed to reduce memory usage and optimize the rendering performance.

Here are listed vertex structures used by the engine:

**Vertex Buffer 0**:
* Vector3 Position

**Vertex Buffer 1**:
* Half2 TexCoord
* Float1010102 Normal
* Float1010102 Tangent
* Half2 LightmapUVs

**Vertex Buffer 2** (*optional*):
* Color32 Color



