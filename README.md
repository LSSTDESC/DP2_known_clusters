# DP2_known_clusters
Gathering DP2 Known Cluster Catalogs &amp; Samples

This is all based on the latest DP2 map viewer shared by TQ and Shrihan. There’s a `dp2_tract` column, which you can use to select clusters in the footprint using `dp2_tract >= 0` . Furthermore, you can use the attached `dp2_dataraw.txt` file to get properties for each of the tracts as follows:

```
import ast
with open("dp2_dataraw.txt", "r") as data:
    dp2_tracts = ast.literal_eval(data.read())
```

The returned object is a list of dictionaries, each of which corresponds to a single tract. The dictionaries have values corresponding to point source depth, extended source depth, number of visits, mean airmass, galactic latitude, and whether it’s in the DESI SGC footprint. The values are given per-band where applicable. It should be pretty straightforward to iterate over the dictionaries and pull out the tracts that satisfy a certain set of conditions.

Note that I left in some old `is_in_dp2` and `is_in_wlss_fields` columns in the catalog for back-compatibility with a few projects, but they are now out of date and tract-based selection is preferred. These columns have been renamed with a LEGACY prefix as a reminder for this
