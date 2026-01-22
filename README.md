
# 2d / 3d

Two and three dimensional examples.

## axis_dependent

These transformations depend on the axes of their input coordinate system. In this case, the input coordinate system is the
array's native coordinate system, which is duplicated.

### mapAxis.zarr

An example using the `rotation` transformation type. Note that the rotation is about the origin.

### byDimension.zarr

An example using the `byDimension` transformation type that itself contains `scale` and `translation` 
transformation types. This is a contrived example for demonstration purposes only.

## basic

These transformations are all either identical to or slight re-expressions of in NGFF v0.4.
All implementations should support these examples.

### identity.zarr

An example using the `identity` transformation type. The physical coordinate system is identical to the array coordinate system.

### scale.zarr

An example using the `scale` transformation type.

### scale_multiscale.zarr

An example of a multiscale image using the `scale` transformation type.

### sequenceScaleTranslation.zarr

An example using the `sequence` transformation type where the sequence contains one `scale` transformation
and one `translation` transformation. 

If an implementation supports all the transformation types contained in a sequence, then that implementation
should also support the sequence.

### sequenceScaleTranslation_multiscale.zarr

An example of a multiscale images using the `sequence` transformation type where the sequence contains one `scale`
transformation and one `translation` transformation. 

If an implementation supports all the transformation types contained in a sequence, then that implementation
should also support the sequence.

The transformations here are identical to those in the `affine_multiscale.zarr` example.

### translation.zarr

An example using the `translation` transformation type.

### scaleParams.zarr

A tranformation of type `scale` using the `path` parameter to reference the zarr array containing its parameters.

### translationParams.zarr

A tranformation of type `translation` using the `path` parameter to reference the zarr array containing its parameters.

## simple

Examples of transformations types that are new, but are simple enough that most implementation should support them.
Specifically they are affines, or subsets of affines.

### affine_multiscales.zarr

An example of a multiscale images using the `affine` transformation type 

The transformations here are identical to those in the `sequenceScaleTranslation_multiscale.zarr` example.

### affine.zarr

An example using the `affine` transformation type.

### affineParams.zarr

An example using the `affine` transformation type for which its parameters are stored in zarr array.

### rotation.zarr

An example using the `rotation` transformation type. Note that the rotation is about the origin.

### rotationParams.zarr

An example using the `rotation` transformation type for which its parameters are stored in zarr array.

## nonlinear

Examples of new, potentially non-linear transformation types. Implementations need not support these transformations.

### invDisplacements.zarr

An example using the `displacements` transformation type.

This transformation is identical to that in the `invCoordinates.zarr`, but represented differently.

### invCoordinates.zarr

An example using the `coordinates` transformation type.

This transformation is identical to that in the `invDisplacements.zarr`, but represented differently.

# user_stories

Examples that are motivated by user stories.

## stitched_tiles_2d

An example in which a set of 2D images tiles are each transformed to a shard "world" coordinate system using a different
(`translation`) coordinate transformation.

## stitched_tiles_3d

An example in which a set of 3D images tiles are each transformed to a shard "world" coordinate system using a different
(`translation`) coordinate transformation.

## image_registration_3d.zarr

An example of a two-step, invertible, non-linear, 3D registration. The two steps of 3D registration represented here were:
first affine, then deformatble. As a result, one direction of the registration is represented as a `sequence` containing 
`affine` and `displacements` transformations. 

Because `displacements` transformations are not closed-form invertible, this example uses a `bijection` transformation 
to indicate that the inverse is stored explicity. 

* a bijection transformation
    * a forward transformation consisting of:
        * a sequence consisting of:
            * a displacement transformation
            * an affine transformation
    * an inverse transformation consisting of:
        * a sequence consisting of:
            * an affine transformation
            * a displacements transformation

## lens_correction.zarr

A realistic example of "lens correction" - apply a 2D, nonlinear tranformation to every slice of a 3D image.
This example using the `byDimension` transformation type that itself contains `displacements` and `identity`
transformation types.

The displacement field for this example is sampled differently (more sparsely) than the image it is applied to.
