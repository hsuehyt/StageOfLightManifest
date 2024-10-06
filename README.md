# StageOfLightManifest

This repository contains a general version of the `manifest.json` file to install the necessary Unity packages for **extOSC** and **KlakSpout** using scoped registries. These packages are specifically used for **Stage of Light**, a 360 projection room at the **NTNU Fine Art Museum**.

## Recommended Unity Version

For optimal performance and compatibility, it is recommended to use **Unity 2021.3 LTS** or higher when running both **extOSC** and **KlakSpout**. These packages rely on newer features and updates in the Unity engine, and using the Long Term Support (LTS) version ensures better stability for production environments.

## Installation Instructions

### Step 1: Update Your `manifest.json`

In most cases, the default `manifest.json` file only contains a `"dependencies"` section. To install the **extOSC** and **KlakSpout** packages, you need to add a new section called `"scopedRegistries"` for Unity to locate the necessary registries.

1. Open your Unity project folder.
2. Navigate to the `Packages` directory.
3. Open the `manifest.json` file with a text editor.
4. **Add the following section** at the top of your `manifest.json` to include the scoped registries for Keijiro and OpenUPM. Ensure it is placed before the `"dependencies"` section:
   
   ```json
   {
     "scopedRegistries": [
       {
         "name": "Keijiro",
         "url": "https://registry.npmjs.com",
         "scopes": [ "jp.keijiro" ]
       },
       {
         "name": "package.openupm.com",
         "url": "https://package.openupm.com",
         "scopes": [ "com.iam1337.extosc" ]
       }
     ],
   ```

5. Next, inside the existing `"dependencies"` section, add the package dependencies for **extOSC** and **KlakSpout** like this:

   ```json
   "dependencies": {
     "jp.keijiro.klak.spout": "2.0.3",
     "com.iam1337.extosc": "1.19.7",
     // Your existing dependencies remain here
   }
   ```

6. **Important**: **Do not add `//` or any symbols** for comments inside the `manifest.json` file, as JSON does not support comments. Any such symbols will cause errors.

7. **Final `manifest.json` Structure**: After editing, your `manifest.json` should have the following structure:

   ```json
   {
     "scopedRegistries": [
       {
         "name": "Keijiro",
         "url": "https://registry.npmjs.com",
         "scopes": [ "jp.keijiro" ]
       },
       {
         "name": "package.openupm.com",
         "url": "https://package.openupm.com",
         "scopes": [ "com.iam1337.extosc" ]
       }
     ],
     "dependencies": {
       "jp.keijiro.klak.spout": "2.0.3",
       "com.iam1337.extosc": "1.19.7",
       // Your existing dependencies should stay here (without `//` or symbols)
     }
   }
   ```

You can view an example of what your `manifest.json` file should look like here:

![manifest.json example](https://github.com/hsuehyt/StageOfLightManifest/blob/main/Snapshots/manifest.png)

8. **Do not erase your existing dependencies!** Simply add the new scoped registries and dependencies as shown above.

### Step 2: Restart Unity

Once you have updated and saved the `manifest.json` file, restart Unity. The Package Manager will automatically install **extOSC** and **KlakSpout**.

### Step 3: Verify Installation

1. Go to **Edit > Project Settings > Package Manager**.
2. Under **Scoped Registries**, verify that both **Keijiro** and **package.openupm.com** are listed.

You should see something like this:

![My Registries](https://github.com/hsuehyt/StageOfLightManifest/blob/main/Snapshots/My%20Registries.png)

3. Open **Window > Package Manager**.
4. In the **Packages** dropdown (top left), select **My Registries**.
5. Verify that both **extOSC** and **KlakSpout** are listed as installed packages.

---

## About the Packages

### extOSC
[extOSC](https://github.com/Iam1337/extOSC) is an Open Sound Control (OSC) library for Unity that enables easy communication between Unity and other software or hardware over a network. For a **360 projection room project**, **extOSC** can be incredibly useful for real-time control and synchronization, such as:

- **Real-Time Interactivity**: You can control various aspects of the Unity project, such as camera movements, lighting, or transitions, using external devices (e.g., MIDI controllers, smartphones, or tablets) that send OSC messages.
- **Synchronization**: With OSC, you can sync the Unity project to external audio, lighting systems, or projection software, making it easier to coordinate real-time events across multiple systems.
- **Live Performances**: extOSC is ideal for live performances, where you can use external software like Ableton Live, VJ applications, or custom OSC controllers to manipulate elements of your 360 projection room in real-time.

---

### KlakSpout
[KlakSpout](https://github.com/keijiro/KlakSpout) allows Unity to send and receive video streams using the **Spout** system, which is widely used for sharing textures between applications in real-time. In the context of a **360 projection room project**, KlakSpout offers several advantages:

- **Video Output to Multiple Screens**: KlakSpout can send your 360-degree content or textures from Unity to external projection software that handles the multiple displays of your projection room. This allows for real-time visuals to be sent to multiple projectors, providing seamless, immersive 360-degree projection.
- **Video Input for Dynamic Content**: You can also bring in real-time video streams from external applications into Unity using KlakSpout, enabling interactive and dynamic content that can respond to live video feeds or media files.
- **Integration with VJ and Projection Mapping Tools**: KlakSpout is compatible with popular VJ applications and projection mapping software (like Resolume), allowing you to integrate Unity-generated visuals with other visual content during live performances or exhibitions.