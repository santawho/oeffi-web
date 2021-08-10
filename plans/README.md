## NETWORK PLANS

This folder is all about the public transport network plans.

Unless otherwise noted, the plans are under a proprietary license. This means if you want to use them you need to ask the copyright holder for permission.
There are some exceptions under a free license, see the plans index file.

### Index

The most important file is [plans-index.txt](plans-index.txt).
Use it to search for plans that already exist, e.g. by name or disclaimer.
You'll find a list of the fields at the top of the file.

* `ID`: This is the most important field, as it needs to match with plan filenames (see below). Although not set in stone, IDs usually start with the city or region name.
* `location` is a WGS84 coordinate of the plan, usually anchored to some kind of main station if it exists.
* `valid_from` is taken from a date that is usually embedded in the plan, or in rare cases written aside the download link. It can designate a day (yyyy-MM-dd), a month (yyyy-MM) or just a year (yyyy).
* `name` again starts with the city or region name, and is what's shown to users.
* `disclaimer` usually contains the entity which owns the plan, or an open source license if it's licensed that way.
* `external_uri` designates an external URI to load the plan image from. If the field is *not* set (as with most plans), the plan image is stored along with the index as well (see next section).

### Plan Images

Plan image files always have their name derived from the plan ID, suffixed by `.png`.
All plans are in PNG format and use 8-bit colormap to optimize traffic and RAM usage while decoding.

Sizes are around 2500×3300 pixels, give or take 1000 on each axis. For plans in portrait orientation, axis are swapped.
Generally if you want to update an existing plan, please don't change the pixel size too much unless there is a reason to.
On Linux, you can use the `file` command to examine the size of existing plans.

It is very much recommended to always use a PDF as the source, if available. Gimp can open PDF directly from remote URLs.
Try "round" pixels/inch values like 100, 200 or 250.
One of those should yield an absolute size that is almost identical to the previous version.
If you're creating a new plan, make sure station names can be read easily when zoomed in.

Format: PNG, 8-bit colormap, pixel size varies

Typical procedure:
* open PDF,
* select proper PPI that yields the desired pixel size (don't resize),
* convert from RGB to 8-bit colormap,
* save as PNG

### Plan Thumbnails

Plan thumbnails have the same characteristics as the images, however their size is 192×192 pixels and the file name suffix is `_thumb.png`.
They try to visually focus on some distinct detail of the respective full plan, such that the plan can be identified by thumbnail more easily.
Thumbnails of inner city plans tend to be zoomed in a bit on some detail, while those of complete network plans usually zoom out a bit more.

Note: For maximum quality, crop and resize the plan in its RGB format into its thumbnail first, then convert the thumbnail into 8-bit colormap as the last step.

Format: PNG, 8-bit colormap, 192×192 pixels

Typical procedure:
* open PDF,
* select PPI,
* crop to a square (1:1 fixed aspect ratio),
* resize to 192×192,
* convert from RGB to 8-bit colormap,
* save as PNG (with `_thumb.png` suffix)
