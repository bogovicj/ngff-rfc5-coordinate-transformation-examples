This folder contains resources that enable you to use an in-development version [BigWarp](https://imagej.net/plugins/bigwarp)
to view images transformed according to the specification in [NGFF's RFC-5.](https://ngff.openmicroscopy.org/rfc/5/)

## View examples with BigWarp

After completing the prerequisites below, 

1. Download the BigWarp project file for the example you are interested in.
2. Run Fiji.
3. Run BigWarp with `Plugins > BigDataViewer › Big Warp Command`
4. In the dialog that appears, enter the path of the project file in the top-most field, labeled `BigWarp project or landmarks`.
5. Press `OK`.

BigWarp will run and display an image; the details will depend on the particular example.

## projects

This folder contains BigWarp project files that will open the examples in this bucket.


### selected BigWarp project files

#### `2d-invDisplacements.json`

Loads the data in:
`s3://ngff-rfc5-coordinate-transformation-examples/2d/nonlinear/invDisplacements.zarr/`

#### `2d-invCoordinates.json`

Loads the data in:
`s3://ngff-rfc5-coordinate-transformation-examples/2d/nonlinear/invCoordinates.zarr/`

#### `3d-invCoordinates.json`

Loads the data in:
`s3://ngff-rfc5-coordinate-transformation-examples/3d/nonlinear/invDisplacements.zarr/`

#### `3d-invDisplacements.json`

Loads the data in:
`s3://ngff-rfc5-coordinate-transformation-examples/3d/nonlinear/invCoordinates.zarr/`

#### `registration-3d-forward.json` 

Loads the data in:
`s3://ngff-rfc5-coordinate-transformation-examples/user_stories/image_registration_3d.zarr/`

and applying the forward transformation to the image `FCWB`

#### `registration-3d-inverse.json` 

Loads the data in:
`s3://ngff-rfc5-coordinate-transformation-examples/user_stories/image_registration_3d.zarr/`

and applying the inverse transformation to the image `JRC2018F`

#### `stitched-tiles-2d.json` 

Loads the data in:
`s3://ngff-rfc5-coordinate-transformation-examples/user_stories/stitched_tiles_2d.zarr/`

Displays tiles in "world" space in the moving window, and "raw" tiles in the fixed window.

#### `stitched-tiles-2d.json` 

Loads the data in:
`s3://ngff-rfc5-coordinate-transformation-examples/user_stories/stitched_tiles_3d.zarr/`

Displays tiles in "world" space in the moving window, and "raw" tiles in the fixed window.

#### `lens-correction.json` 

Loads the data in:
`s3://ngff-rfc5-coordinate-transformation-examples/user_stories/lens_correction.zarr/`

Displays a transformed image in the moving window and the "raw" image in the fixed window.

## Prerequisites

**Note: The code running these examples is under active development. If something doesn't work, Check if there are newer versions
of the code here and re-run these setup steps if so.** 

The code was most recently updated on 4 April 2025.

Setup your Fiji.

BigWarp is a Fiji plugin. This is how to modify your Fiji installation with the in-development version of bigwarp needed to
view these examples.

### automatic

Run the `installToFiji` script, passing the path to your Fiji installation as an argument.
We recommend creating a copy of your Fiji and using that copy for this demo, for example:

```
./installToFiji ~/packages/Fiji.app_ngff
```

### manual

1. Download the jar files in the `jars` folder
2. Copy them into the `jars` folder in your Fiji installation.
3. Delete all jars that are 
4. Download the jar files in the `plugins` folder
5. Copy them into the `plugins` folder in your Fiji installation.
6. Delete older jars
