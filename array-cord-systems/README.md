# Option A

To work in pixel coordinates, 

1. explicitly make an "array coordinate system" 
2. indicate which array it refers to with an `identity` transformation
3. refer to the explicit array coordinate system from the scene

## Note

The array coordinate system does not have to refer to the highest resolution zarr array in the multiscales.
E.g. in the `target` multiscales metadata, `s1` is the `pixel` coordinate system.


# Option B

To work in pixel coordinates, "manually" add appropriate physical to pixel transformations in the scene metadata.
