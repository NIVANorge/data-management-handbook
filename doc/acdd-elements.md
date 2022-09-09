Creating NetCDF-CF files
========================

By documenting and formatting your data using [NetCDF](#netcdf)
following the [CF conventions](https://cfconventions.org/) and the
[Attribute Convention for Data Discovery
(ACDD)](https://wiki.esipfed.org/Attribute_Convention_for_Data_Discovery_1-3),
[MMD](#mmd) files can be automatically generated from the
[NetCDF](#netcdf) files. The [CF conventions](#cf) is a controlled
vocabulary providing a definitive description of what the data in each
variable represents, and the spatial and temporal properties of the
data. The [ACDD](#acdd) vocabulary describes attributes recommended for
describing a [NetCDF](#netcdf) dataset to data discovery systems. See,
e.g., [netCDF4-python docs](https://unidata.github.io/netcdf4-python/),
or [xarray docs](http://xarray.pydata.org/en/stable/user-guide/io.html)
for documentation about how to create netCDF files.

The ACDD recommendations should be followed in order to properly
document your netCDF-CF files. The below tables summarize required and
recommended ACDD and some additional attributes that are needed to
properly populate a discovery metadata catalog which fulfills the
requirements of international standards (e.g., GCMD/DIF, the INSPIRE and
WMO profiles of ISO19115, etc.).

Notes
-----

**Keywords** describe the content of your dataset following a given
vocabulary. You may use any vocabularies to define your keywords, but a
link to the keyword definitions should be provided in the
\`\`keywords\_vocabulary\`\` attribute. This attribute provides
information about the vocabulary defining the keywords used in the
\`\`keywords\`\` attribute. Example:

:keywords\_vocabulary = "GCMDSK:GCMD Science
Keywords:https://gcmd.earthdata.nasa.gov/kms/concepts/concept\_scheme/sciencekeywords,
GEMET:INSPIRE Themes:http://inspire.ec.europa.eu/theme,
NORTHEMES:GeoNorge
Themes:https://register.geonorge.no/metadata-kodelister/nasjonal-temainndeling"
;

Note that the **GCMDSK**, **GEMET** and **NORTHEMES** vocabularies are
required for indexing in [S-ENDA](https://adc.met.no/) and
[Geonorge](https://www.geonorge.no/en/). You may find appropriate
keywords at the following links:

-   [GCMDSK](https://gcmd.earthdata.nasa.gov/kms/concepts/concept_scheme/sciencekeywords)

-   [GEMET](http://inspire.ec.europa.eu/theme)

-   [NORTHEMES](https://register.geonorge.no/metadata-kodelister/nasjonal-temainndeling)

The keywords should be provided by the \`\`keywords\`\` attribute as a
comma separated list with a short name defining the vocabulary used,
followed by the actual keyword, i.e., \`\`short\_name:keyword\`\`.
Example:

:keywords = "GCMDSK:Earth Science &gt; Atmosphere &gt; Atmospheric
radiation, GEMET:Meteorological geographical features, GEMET:Atmospheric
conditions, NORTHEMES:Weather and climate" ;

See <https://adc.met.no/node/96> for more information about how to
define the ACDD keywords.

A data **license** provides information about any restrictions on the
use of the dataset. To support a linked data approach, the
\`\`license\`\` element should be supported by a
\`\`license\_resource\`\` element, providing a link to the license
definition. Example:

:license = "CC-BY-4.0" ;  
:license\_resource = "http://spdx.org/licenses/CC-BY-4.0" ;

List of Attributes
------------------

This section provides lists of ACDD elements that are required and
recommended, as well as some extra elements that are needed to fully
support our data management needs. The right columns of these tables
provide the [MET Norway Metadata Specification
(MMD)](https://htmlpreview.github.io/?https://github.com/metno/mmd/blob/master/doc/mmd-specification.html)
fields that map to the ACDD (and our extension to ACDD) elements. Please
refer to
[MMD](https://htmlpreview.github.io/?https://github.com/metno/mmd/blob/master/doc/mmd-specification.html)
for definitions of these elements, as well as controlled vocabularies
that should be used. Note that the below tables are automatically
generated - check
<https://github.com/metno/py-mmd-tools/blob/master/py_mmd_tools/mmd_elements.yaml>
if anything is unclear.

In order to check your netCDF-CF files, and to create MMD xml files, you
can use the nc2mmd.py script in the
[py-mmd-tools](https://github.com/metno/py-mmd-tools) Python package.

The following ACDD elements are required:

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p><strong>ACDD Attribute</strong></p></td>
<td style="text-align: left;"><p><strong>MMD equivalent</strong></p></td>
<td style="text-align: left;"><p><strong>Comment</strong></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>id</p></td>
<td style="text-align: left;"><p>metadata_identifier</p></td>
<td style="text-align: left;"><p>Required, and should be UUID. No repetition allowed.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>naming_authority</p></td>
<td style="text-align: left;"><p>metadata_identifier</p></td>
<td style="text-align: left;"><p>Required. We recommend using reverse-DNS naming. No repetition allowed.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>date_created</p></td>
<td style="text-align: left;"><p>last_metadata_update&gt;update&gt;datetime</p></td>
<td style="text-align: left;"><p>Format as ISO8601.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>title</p></td>
<td style="text-align: left;"><p>title&gt;title</p></td>
<td style="text-align: left;"><p>Use ACDD extension "title_no" for Norwegian translation.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>summary</p></td>
<td style="text-align: left;"><p>abstract&gt;abstract</p></td>
<td style="text-align: left;"><p>Use ACDD extension "summary_no" for Norwegian translation.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>time_coverage_start</p></td>
<td style="text-align: left;"><p>temporal_extent&gt;start_date</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>geospatial_lat_max</p></td>
<td style="text-align: left;"><p>geographic_extent&gt;rectangle&gt;north</p></td>
<td style="text-align: left;"><p>No repetition allowed.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>geospatial_lat_min</p></td>
<td style="text-align: left;"><p>geographic_extent&gt;rectangle&gt;south</p></td>
<td style="text-align: left;"><p>No repetition allowed.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>geospatial_lon_max</p></td>
<td style="text-align: left;"><p>geographic_extent&gt;rectangle&gt;east</p></td>
<td style="text-align: left;"><p>No repetition allowed.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>geospatial_lon_min</p></td>
<td style="text-align: left;"><p>geographic_extent&gt;rectangle&gt;west</p></td>
<td style="text-align: left;"><p>No repetition allowed.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>keywords</p></td>
<td style="text-align: left;"><p>keywords&gt;keyword</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>keywords_vocabulary</p></td>
<td style="text-align: left;"><p>keywords&gt;vocabulary</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
</tbody>
</table>

The following ACDD elements are (highly) recommended:

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p><strong>ACDD Attribute</strong></p></td>
<td style="text-align: left;"><p><strong>Default</strong></p></td>
<td style="text-align: left;"><p><strong>MMD equivalent</strong></p></td>
<td style="text-align: left;"><p><strong>Comment</strong></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>date_metadata_modified</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>last_metadata_update&gt;update&gt;datetime</p></td>
<td style="text-align: left;"><p>Format as ISO8601. Comma separated list if more than once.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>time_coverage_end</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>temporal_extent&gt;end_date</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>geospatial_bounds</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>geographic_extent&gt;polygon</p></td>
<td style="text-align: left;"><p>No repetition allowed.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>processing_level</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>operational_status</p></td>
<td style="text-align: left;"><p>No repetition allowed. See the MMD docs for valid keywords.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>license</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>use_constraint&gt;identifier</p></td>
<td style="text-align: left;"><p>No repetition allowed.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>creator_role</p></td>
<td style="text-align: left;"><p>Investigator</p></td>
<td style="text-align: left;"><p>personnel&gt;role</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>contributor_role</p></td>
<td style="text-align: left;"><p>Investigator</p></td>
<td style="text-align: left;"><p>personnel&gt;role</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>creator_name</p></td>
<td style="text-align: left;"><p>Not available</p></td>
<td style="text-align: left;"><p>personnel&gt;name</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>contributor_name</p></td>
<td style="text-align: left;"><p>Not available</p></td>
<td style="text-align: left;"><p>personnel&gt;name</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>creator_email</p></td>
<td style="text-align: left;"><p>Not available</p></td>
<td style="text-align: left;"><p>personnel&gt;email</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>creator_institution</p></td>
<td style="text-align: left;"><p>Not available</p></td>
<td style="text-align: left;"><p>personnel&gt;organisation</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>institution</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>data_center&gt;data_center_name&gt;long_name</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>publisher_url</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>data_center&gt;data_center_url</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>project</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>project&gt;long_name</p></td>
<td style="text-align: left;"><p>Semicolon separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>platform</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>platform&gt;long_name</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>platform_vocabulary</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>platform&gt;resource</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>instrument</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>platform&gt;instrument&gt;long_name</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>instrument_vocabulary</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>platform&gt;instrument&gt;resource</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>source</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>activity_type</p></td>
<td style="text-align: left;"><p>Semicolon separated list.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>creator_name</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>dataset_citation&gt;author</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>date_created</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>dataset_citation&gt;publication_date</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>title</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>dataset_citation&gt;title</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>publisher_name</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>dataset_citation&gt;publisher</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>metadata_link</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>dataset_citation&gt;url</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>references</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>dataset_citation&gt;other</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
</tbody>
</table>

The following elements are ACDD extensions that are needed to improve
(meta)data interoperability. Please refer to the documentation of
[MMD](https://htmlpreview.github.io/?https://github.com/metno/mmd/blob/master/doc/mmd-specification.html)
for more details:

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p><strong>Necessary non-ACDD Attribute</strong></p></td>
<td style="text-align: left;"><p><strong>Default</strong></p></td>
<td style="text-align: left;"><p><strong>MMD equivalent</strong></p></td>
<td style="text-align: left;"><p><strong>Comment</strong></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>spatial_representation</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>spatial_representation</p></td>
<td style="text-align: left;"><p>No repetition allowed.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>alternate_identifier</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>alternate_identifier&gt;alternate_identifier</p></td>
<td style="text-align: left;"><p>Alternative identifier for the dataset (but not DOI). Comma separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>alternate_identifier_type</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>alternate_identifier&gt;type</p></td>
<td style="text-align: left;"><p>Identification of the type of identifier used. Comma separated list.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>date_metadata_modified_type</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>last_metadata_update&gt;update&gt;type</p></td>
<td style="text-align: left;"><p>E.g., major or minor modification. Comma separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>date_created_type</p></td>
<td style="text-align: left;"><p>Created</p></td>
<td style="text-align: left;"><p>last_metadata_update&gt;update&gt;type</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>title_no</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>title&gt;title</p></td>
<td style="text-align: left;"><p>Used for Norwegian version of the title.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>title_lang</p></td>
<td style="text-align: left;"><p>en</p></td>
<td style="text-align: left;"><p>title&gt;lang</p></td>
<td style="text-align: left;"><p>ISO language code.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>summary_no</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>abstract&gt;abstract</p></td>
<td style="text-align: left;"><p>Used for Norwegian version of the abstract.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>summary_lang</p></td>
<td style="text-align: left;"><p>en</p></td>
<td style="text-align: left;"><p>abstract&gt;lang</p></td>
<td style="text-align: left;"><p>ISO language code.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>dataset_production_status</p></td>
<td style="text-align: left;"><p>Complete</p></td>
<td style="text-align: left;"><p>dataset_production_status</p></td>
<td style="text-align: left;"><p>No repetition allowed.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>access_constraint</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>access_constraint</p></td>
<td style="text-align: left;"><p>No repetition allowed.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>license_resource</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>use_constraint&gt;resource</p></td>
<td style="text-align: left;"><p>No repetition allowed.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>contributor_email</p></td>
<td style="text-align: left;"><p>Not available</p></td>
<td style="text-align: left;"><p>personnel&gt;email</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>contributor_institution</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>personnel&gt;organisation</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>contributor_organisation</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>personnel&gt;organisation</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>institution_short_name</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>data_center&gt;data_center_name&gt;short_name</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>related_dataset_id</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>related_dataset&gt;related_dataset</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>related_dataset_relation_type</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>related_dataset&gt;relation_type</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>iso_topic_category</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>iso_topic_category</p></td>
<td style="text-align: left;"><p>Comma separated list.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>project_short_name</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>project&gt;short_name</p></td>
<td style="text-align: left;"><p>Semicolon separated list.</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>quality_control</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>quality_control</p></td>
<td style="text-align: left;"><p>No repetition allowed.</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>doi</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>dataset_citation&gt;doi</p></td>
<td style="text-align: left;"></td>
</tr>
</tbody>
</table>
