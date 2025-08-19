# <center><u>CameraTracker Settings</u></center>

<img src="https://cgmatter.github.io/Public/Images/CameraTracker/cameratrackersettings.png" style="border-radius:12px; border:2px solid orange;">
<br><br>

<ul>
  <li><b style="color:orange">Help</b> - Opens the documentation.</li>
  <li><b style="color:orange">Log</b> - Used for obtaining log (cmd for Windows and terminal for Mac).</li>
  <li><b style="color:orange">Images from Video</b> - Converts any video into an image sequence.</li>
  <li><b style="color:orange">Mask Actor</b> - Runs rotomation on the image sequence.</li>
  <li><b style="color:orange">Image Sequence</b> - Directory where your image sequence is.</li>
  <li><b style="color:orange">Alpha</b> - Uses alpha of image sequence as a mask.</li>
  <li><b style="color:orange">Undistort</b> - Undistorts the sequence for a better solve.</li>
  <li><b style="color:orange">Densify</b> - Creates a dense colored point cloud (<i>undistort must be enabled</i>).</li>
  <li><b style="color:orange">Zoom</b> - Enable if you zoom in/out at any point.</li>
  <li><b style="color:orange">Shaky</b> - Better orientation calculation. Good for handheld shots.</li>
  <li><b style="color:orange">Refine</b> - Create higher quality trackers.</li>
  <li><b style="color:orange">Max Resolution</b> - Maximum resolution used for tracking (reduce for speedups).</li>
  <li><b style="color:orange">Features</b> - Maximum number of features to extract per frame.</li>
  <li><b style="color:orange">Smart Overlap</b> - Adds cross check, quadratic frame spacing, and 2-way matching.</li>
  <li><b style="color:orange">Overlap</b> - Number of frames to look ahead for matching.</li>
  <li><b style="color:orange">Insane Mode</b> - Uses comprehensive matching (all pairs). This is <i>VERY SLOW</i>. Use at your own risk!</li>
  <li><b style="color:orange">Advanced Settings</b> - Fine grain controls of the matching/solving.</li>
  <li><b style="color:orange">Cuda</b> - Uses Cuda enabled graphics card (<i>must be an NVidia card</i>).</li>
  <li><b style="color:orange">Clean Points</b> - Removes outliers from selected point cloud.</li>
  <li><b style="color:orange">Invert</b> - Inverts Camera <-> Object motion.</li>
  <li><b style="color:orange">Reset</b> - Clears database and extra files (do this before resolving).</li>
</ul>




# <center><u>CameraTracker Errors</u></center>

All errors are a result of:

1. An issue with the footage.
2. An issue with installation/use.

## ⚠️ <u>Error Message ≠ Cause of Error</u>

Almost always your error message will say:

>RuntimeError: Error: Python: Traceback
 
or

>Can't find scene_dense.ply

Note that any issue in feature extraction, matching, solving, densifying will eventually *result in these same final errors messages*.

So really:

>RuntimeError: Error: Python: Traceback (most recent call last):
File "/Users/yourusername/Library/Application Support/Blender/4.5/extensions/user_default/camera_tracker_macos/__init__.py", line 569, in invoke
 return self.execute(context)

**tells us absolutely nothing**. The problem is usually more subtle. That's why the **FULL LOG** is much more useful.

## 🎞️ <u>Footage Issues</u>

Generally, **bad footage = bad solve**.

### <center>The *best Solution is always to film again!*</center>

**CameraTracker** uses [photogrammetry](https://en.wikipedia.org/wiki/Photogrammetry) under the hood, so the same principles apply. Here are the common pitfalls:

- <span style="color:orange">**Prominant Moving Objects**</span> - person in the foreground, cars, leaves and grass rustling.
    - <span style="color:lightgreen">Solution: mask out these subjects.</span>
- <span style="color:orange">**Large Reflective Objects**</span> - windows, shiny floors, metal.
    - <span style="color:lightgreen">Solution: mask out these reflections.</span>
- <span style="color:orange">**Zero Parallax**</span> - tripod shots, no movement, very distant scenery.
    - <span style="color:lightgreen">Solution: Film with at least some [parallax](https://en.wikipedia.org/wiki/Parallax) - try the *insane mode* matcher.</span>
- <span style="color:orange">**Large Featureless Surfaces**</span> - blank walls, greenscreens, plain backgrounds.
    - <span style="color:lightgreen">Solution: Try increasing *features to 8000* and *overlap to 30*.</span>
- <span style="color:orange">**Low Quality Footage**</span> - motion blur, heavy grain, low resolution.
    - <span style="color:lightgreen">Solution: Capture better footage.</span>
- <span style="color:orange">**Dramatic lighting changes**</span> - lens flares, indoor-to-outdoor, fast moving lights.
    - <span style="color:lightgreen">Solution: Mask out lens flares - film on manual settings (no autoexposure).</span>

You'll find that fixing these issues will almost always fix your solve.

## ⚙️ <u>Installation/Use Issues</u>

Go to the [product page](https://superhivemarket.com/products/camera-tracker) for compatibility and installation instructions. Here are the most common issues:

- <span style="color:orange">**Sequence In Wrong Drive**</span> - footage on D:/, external SSD, cloud drives.
    - <span style="color:lightgreen">Solution: Put the sequence on the same drive as Blender (usually C:/).
- <span style="color:orange">**Unconventional Filepaths**</span> - exotic characters (è,é,ê,ë), spaces, non-english characters.
    - <span style="color:lightgreen">Solution: Fix your filepath to avoid these cases.
- <span style="color:orange">**Wrong Sequence Names**</span> - 1.jpg, image1.png, frame_1.tiff.
    - <span style="color:lightgreen">Solution: Image sequences should always follow the convention name_0001.png, name_0002.png, etc. (can be other image formats and any name).

- <span style="color:orange">**Wrong OS**</span> - installing MacOS on Windows - installing Windows on MacOS.
    - <span style="color:lightgreen">Solution: Uninstall the addon, download the compatible version and reinstall.
- <span style="color:orange">**Blender Compatibility**</span> - Blender not from [Blender.org](https://www.blender.org), old versions, portable versions.
    - <span style="color:lightgreen">Solution: Only use non-portable Blender 4.3+ official builds (no Microsoft Store, etc.).

---
### *Before contacting me (at [BlenderMarket/Superhive](https://superhivemarket.com/products/camera-tracker)), see if you can resolve the issue first!*