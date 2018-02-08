# Skyrim Texture & Normal Map Guide

v1.0.0
Written 2018 by ciathyza

This guide provides a step-by-step walkthrough for creating optimized HD textures for Skyrim by applying best practices to the texture creation process.

## Requirements

  - [Photoshop](https://www.adobe.com/products/photoshop.html)
  - [NVIDIA Texture Tools for Photoshop](https://developer.nvidia.com/nvidia-texture-tools-adobe-photoshop)
  - [Shadermap Pro](https://shadermap.com/)

## Optional Tools

  - [PixPlant](https://www.pixplant.com/)
  - [DDSOpt](https://www.nexusmods.com/skyrim/mods/5755/)
  - [Ordenador (Skyrim Texture Optimizer)](https://www.nexusmods.com/skyrim/mods/12801)

## Process

### Source Image

  1. Decide the source image used for the texture.
  2. Change the image to 72dpi if it's not.
  3. Prepare source image: adjust rotation, fix distortion, adjust colors, etc.
  4. Make source image seamless, if necessary, either in Photoshop or with a tool like PixPlant.
  5. Save source image as PSD.

### Diffuse Map

  1. Load the source image into Photoshop and flatten it if necessary.
  2. Resize the image to 2048 x 2048.
  3. Save 2k image version as either DDS DX1 (if image has no transparent areas) or as DXT5 (if image has transparent areas). Be sure to enable mip-map generation! Also save the image as PNG for backup.
  4. Undo source image to original image size, then resize to 1024 x 1024.
  5. Save 1k image version as PNG (we will use this for the normal map).

### Normal Map

  1. Load the 1k image into Shadermap Pro.
  2. Remove the ambient occlusion map.
  3. Select the normal map and adjust the intensity value to your liking. Turn Sharpen on.
  4. Select the specular map and adjust the specular value. Setting it darker will remove shininess while setting it brighter will increase shininess. Setting to it to 0 (RGB 127, 127, 127) will create a neutral specularity.
  5. Save the normal map as TGA with alpha channel.
  6. Save the specular map as TGA.
  7. Open normal map and specular map in Photoshop.
  8. Copy the specular map image and paste it into the alpha channel of the normal map image.
  9. Save the normal map image in either 8.8.8.8. uncompressed or in DXT5 format, incl. mip-maps. The choice depends on how important detail in the normal map is for your texture. Using DXT5 will compress the normal map and will reduce the quality of the normal map.
  10. Rename the normal map file to reflect the diffuse map file name plus '_n'.

## DDS Format Size Table

| Resolution | DXT1    | DXT1 Alpha | DXT3    | DXT5    | 4.4.4.4 ARGB | 8.8.8. RGB | 8.8.8.8. Uncompressed |
|:-----------|:--------|:-----------|:--------|:--------|:-------------|:-----------|:----------------------|
| 512        | 171KB   | 171KB      | 342KB   | 342KB   | 684KB        | 1024KB     | 1368KB                |
| 1024       | 684KB   | 684KB      | 1368KB  | 1368KB  | 2732KB       | 4096KB     | 5464KB                |
| 2048       | 2732KB  | 2732KB     | 5464KB  | 5464KB  | 10.67MB      | 16MB       | 21.34MB               |
| 4096       | 10.67MB | 10.67MB    | 21.34MB | 21.34MB | 42.68MB      | 64MB       | 85.37MB               |

