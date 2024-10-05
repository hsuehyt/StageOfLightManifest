# StageOfLightManifest

This repository contains a general version of the `manifest.json` file to install the necessary Unity packages for **extOSC** and **KlakSpout** using scoped registries.

## Installation Instructions

### Step 1: Update Your `manifest.json`

1. Open your Unity project folder.
2. Navigate to the `Packages` directory.
3. Open the `manifest.json` file with a text editor.
4. **Do not erase your existing dependencies!** Add the following sections from this repository’s `manifest.json`:
   
   #### Scoped Registries Section:
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
     ]
   }
   ```
   
   #### Dependencies Section:
   ```json
   {
     "jp.keijiro.klak.spout": "2.0.3",
     "com.iam1337.extosc": "1.19.7"
   }
   ```
   
   - **Make sure to add this into the existing `"scopedRegistries"` and `"dependencies"` sections** of your `manifest.json`. Don’t overwrite the entire file to avoid losing important dependencies needed for your project.

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