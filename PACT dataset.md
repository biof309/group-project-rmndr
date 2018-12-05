

```python
### Import packages to pull json files from web
import requests
import pandas as pd
import numpy as np
from sqlalchemy import create_engine
import matplotlib.pyplot as plt
```


```python
### Assign URL to variable: url
url = 'https://services7.arcgis.com/vA61DZby76ncaItU/ArcGIS/rest/services/Family_PACT_Providers_File/FeatureServer/0?f=pjson'
```


```python
### Package the request, send the request and catch the response: r
r = requests.get(url)
```


```python
### Decode the json data into a dictionary: json_data
json_data = r.json()
```


```python
### Print each key-value in json_data
for k in json_data.keys():
    print(k + ':', json_data[k])
```

    currentVersion: 10.61
    id: 0
    name: Family_PACT_Providers_File
    type: Feature Layer
    serviceItemId: a2742f60dd944a1fa49377bd0e8a7772
    displayField: 
    description: 
    copyrightText: 
    defaultVisibility: True
    editingInfo: {'lastEditDate': 1535065600244}
    relationships: []
    isDataVersioned: False
    supportsAppend: True
    supportsCalculate: True
    supportsTruncate: True
    supportsAttachmentsByUploadId: True
    supportsAttachmentsResizing: True
    supportsRollbackOnFailureParameter: True
    supportsStatistics: True
    supportsAdvancedQueries: True
    supportsValidateSql: True
    supportsCoordinatesQuantization: True
    supportsQuantizationEditMode: True
    supportsApplyEditsWithGlobalIds: False
    advancedQueryCapabilities: {'supportsPagination': True, 'supportsPaginationOnAggregatedQueries': True, 'supportsQueryRelatedPagination': True, 'supportsQueryWithDistance': True, 'supportsReturningQueryExtent': True, 'supportsStatistics': True, 'supportsOrderBy': True, 'supportsDistinct': True, 'supportsQueryWithResultType': True, 'supportsSqlExpression': True, 'supportsAdvancedQueryRelated': True, 'supportsCountDistinct': True, 'supportsLod': True, 'supportsReturningGeometryCentroid': False, 'supportsQueryWithDatumTransformation': True, 'supportsHavingClause': True, 'supportsOutFieldSQLExpression': True, 'supportsMaxRecordCountFactor': True, 'supportsTopFeaturesQuery': True}
    useStandardizedQueries: True
    geometryType: esriGeometryPoint
    minScale: 18489298
    maxScale: 0
    extent: {'xmin': -13832780.561202928, 'ymin': 3836834.839842052, 'xmax': -12757185.035800016, 'ymax': 5155621.728620415, 'spatialReference': {'wkid': 102100, 'latestWkid': 3857}}
    drawingInfo: {'renderer': {'type': 'simple', 'symbol': {'type': 'esriPMS', 'url': 'RedSphere.png', 'imageData': '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', 'contentType': 'image/png', 'width': 15, 'height': 15}}}
    allowGeometryUpdates: True
    hasAttachments: False
    htmlPopupType: esriServerHTMLPopupTypeNone
    hasM: False
    hasZ: False
    objectIdField: FID
    uniqueIdField: {'name': 'FID', 'isSystemMaintained': True}
    globalIdField: 
    typeIdField: 
    fields: [{'name': 'Provider_Number', 'type': 'esriFieldTypeInteger', 'actualType': 'int', 'alias': 'Provider Number', 'sqlType': 'sqlTypeInteger', 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'NPI_Provider_Number', 'type': 'esriFieldTypeInteger', 'actualType': 'int', 'alias': 'NPI Provider Number', 'sqlType': 'sqlTypeInteger', 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Owner_Number', 'type': 'esriFieldTypeInteger', 'actualType': 'int', 'alias': 'Owner Number', 'sqlType': 'sqlTypeInteger', 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Service_Location_Number', 'type': 'esriFieldTypeInteger', 'actualType': 'int', 'alias': 'Service Location Number', 'sqlType': 'sqlTypeInteger', 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Businness_Legal_Name', 'type': 'esriFieldTypeString', 'actualType': 'nvarchar', 'alias': 'Provider Businness/Legal Name', 'sqlType': 'sqlTypeNVarchar', 'length': 256, 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Enrollment_Status_Effective_dat', 'type': 'esriFieldTypeDate', 'actualType': 'datetime2', 'alias': 'Enrollment Status Effective date', 'sqlType': 'sqlTypeTimestamp2', 'length': 8, 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Type_Code', 'type': 'esriFieldTypeInteger', 'actualType': 'int', 'alias': 'Provider Type Code', 'sqlType': 'sqlTypeInteger', 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Type_Code_Desc', 'type': 'esriFieldTypeString', 'actualType': 'nvarchar', 'alias': 'Provider Type Code Desc', 'sqlType': 'sqlTypeNVarchar', 'length': 256, 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_License_Number', 'type': 'esriFieldTypeString', 'actualType': 'nvarchar', 'alias': 'Provider License Number', 'sqlType': 'sqlTypeNVarchar', 'length': 256, 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Specialty_Code', 'type': 'esriFieldTypeInteger', 'actualType': 'int', 'alias': 'Provider Specialty Code', 'sqlType': 'sqlTypeInteger', 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Specialty_Code_Desc', 'type': 'esriFieldTypeString', 'actualType': 'nvarchar', 'alias': 'Provider Specialty Code Desc', 'sqlType': 'sqlTypeNVarchar', 'length': 256, 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Out_of_State_Ind', 'type': 'esriFieldTypeInteger', 'actualType': 'int', 'alias': 'Out of State Ind', 'sqlType': 'sqlTypeInteger', 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Out_of_State_Desc', 'type': 'esriFieldTypeString', 'actualType': 'nvarchar', 'alias': 'Out of State Desc', 'sqlType': 'sqlTypeNVarchar', 'length': 256, 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Address_County_Code', 'type': 'esriFieldTypeInteger', 'actualType': 'int', 'alias': 'Provider Address County Code', 'sqlType': 'sqlTypeInteger', 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Address_County_Code_De', 'type': 'esriFieldTypeString', 'actualType': 'nvarchar', 'alias': 'Provider Address County Code Desc', 'sqlType': 'sqlTypeNVarchar', 'length': 256, 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Address_Attention_Line', 'type': 'esriFieldTypeString', 'actualType': 'nvarchar', 'alias': 'Provider Address Attention Line', 'sqlType': 'sqlTypeNVarchar', 'length': 256, 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Address_Line_1', 'type': 'esriFieldTypeString', 'actualType': 'nvarchar', 'alias': 'Provider Address Line 1', 'sqlType': 'sqlTypeNVarchar', 'length': 256, 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Address_Line_2', 'type': 'esriFieldTypeString', 'actualType': 'nvarchar', 'alias': 'Provider Address Line 2', 'sqlType': 'sqlTypeNVarchar', 'length': 256, 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Address_City', 'type': 'esriFieldTypeString', 'actualType': 'nvarchar', 'alias': 'Provider Address City', 'sqlType': 'sqlTypeNVarchar', 'length': 256, 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Address_State', 'type': 'esriFieldTypeString', 'actualType': 'nvarchar', 'alias': 'Provider Address State', 'sqlType': 'sqlTypeNVarchar', 'length': 256, 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Address_Zip', 'type': 'esriFieldTypeInteger', 'actualType': 'int', 'alias': 'Provider Address Zip', 'sqlType': 'sqlTypeInteger', 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Address_Latitude', 'type': 'esriFieldTypeDouble', 'actualType': 'float', 'alias': 'Provider Address Latitude', 'sqlType': 'sqlTypeFloat', 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'Provider_Address_Longitude', 'type': 'esriFieldTypeDouble', 'actualType': 'float', 'alias': 'Provider Address Longitude', 'sqlType': 'sqlTypeFloat', 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'MSSA_ID', 'type': 'esriFieldTypeString', 'actualType': 'nvarchar', 'alias': 'MSSA_ID', 'sqlType': 'sqlTypeNVarchar', 'length': 256, 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'TRACT_ID', 'type': 'esriFieldTypeDouble', 'actualType': 'float', 'alias': 'TRACT_ID', 'sqlType': 'sqlTypeFloat', 'nullable': True, 'editable': True, 'domain': None, 'defaultValue': None}, {'name': 'FID', 'type': 'esriFieldTypeOID', 'actualType': 'int', 'alias': 'FID', 'sqlType': 'sqlTypeInteger', 'nullable': False, 'editable': False, 'domain': None, 'defaultValue': None}]
    indexes: [{'name': 'PK__FAMILY_P__C1BEA5A245D56F6F', 'fields': 'FID', 'isAscending': True, 'isUnique': True, 'description': 'clustered, unique, primary key'}, {'name': 'user_37801.FAMILY_PACT_PROVIDERS_FILE_FAMILY_PACT_PROVIDERS_FILE_Shape_sidx', 'fields': 'Shape', 'isAscending': False, 'isUnique': False, 'description': 'Shape Index'}]
    types: []
    templates: [{'name': 'New Feature', 'description': '', 'drawingTool': 'esriFeatureEditToolPoint', 'prototype': {'attributes': {'Provider_Number': None, 'NPI_Provider_Number': None, 'Owner_Number': None, 'Service_Location_Number': None, 'Provider_Businness_Legal_Name': None, 'Enrollment_Status_Effective_dat': None, 'Provider_Type_Code': None, 'Provider_Type_Code_Desc': None, 'Provider_License_Number': None, 'Provider_Specialty_Code': None, 'Provider_Specialty_Code_Desc': None, 'Out_of_State_Ind': None, 'Out_of_State_Desc': None, 'Provider_Address_County_Code': None, 'Provider_Address_County_Code_De': None, 'Provider_Address_Attention_Line': None, 'Provider_Address_Line_1': None, 'Provider_Address_Line_2': None, 'Provider_Address_City': None, 'Provider_Address_State': None, 'Provider_Address_Zip': None, 'Provider_Address_Latitude': None, 'Provider_Address_Longitude': None, 'MSSA_ID': None, 'TRACT_ID': None}}}]
    supportedQueryFormats: JSON, geoJSON, PBF
    hasStaticData: True
    maxRecordCount: 2000
    standardMaxRecordCount: 32000
    tileMaxRecordCount: 8000
    maxRecordCountFactor: 1
    capabilities: Query
    


```python
print(np.shape('json_data'))
```

    ()
    


```python
### import the local csv file as: pact_data
pact_data = 'Family_PACT_Providers_File.csv'
data = pd.read_csv(pact_data)
data.head()

```


    ---------------------------------------------------------------------------

    FileNotFoundError                         Traceback (most recent call last)

    <ipython-input-11-b168c2dfdef0> in <module>()
          1 ### import the local csv file as: pact_data
          2 pact_data = 'Family_PACT_Providers_File.csv'
    ----> 3 data = pd.read_csv(pact_data)
          4 data.head()
    

    C:\Users\Public\Anaconda3\lib\site-packages\pandas\io\parsers.py in parser_f(filepath_or_buffer, sep, delimiter, header, names, index_col, usecols, squeeze, prefix, mangle_dupe_cols, dtype, engine, converters, true_values, false_values, skipinitialspace, skiprows, nrows, na_values, keep_default_na, na_filter, verbose, skip_blank_lines, parse_dates, infer_datetime_format, keep_date_col, date_parser, dayfirst, iterator, chunksize, compression, thousands, decimal, lineterminator, quotechar, quoting, escapechar, comment, encoding, dialect, tupleize_cols, error_bad_lines, warn_bad_lines, skipfooter, doublequote, delim_whitespace, low_memory, memory_map, float_precision)
        676                     skip_blank_lines=skip_blank_lines)
        677 
    --> 678         return _read(filepath_or_buffer, kwds)
        679 
        680     parser_f.__name__ = name
    

    C:\Users\Public\Anaconda3\lib\site-packages\pandas\io\parsers.py in _read(filepath_or_buffer, kwds)
        438 
        439     # Create the parser.
    --> 440     parser = TextFileReader(filepath_or_buffer, **kwds)
        441 
        442     if chunksize or iterator:
    

    C:\Users\Public\Anaconda3\lib\site-packages\pandas\io\parsers.py in __init__(self, f, engine, **kwds)
        785             self.options['has_index_names'] = kwds['has_index_names']
        786 
    --> 787         self._make_engine(self.engine)
        788 
        789     def close(self):
    

    C:\Users\Public\Anaconda3\lib\site-packages\pandas\io\parsers.py in _make_engine(self, engine)
       1012     def _make_engine(self, engine='c'):
       1013         if engine == 'c':
    -> 1014             self._engine = CParserWrapper(self.f, **self.options)
       1015         else:
       1016             if engine == 'python':
    

    C:\Users\Public\Anaconda3\lib\site-packages\pandas\io\parsers.py in __init__(self, src, **kwds)
       1706         kwds['usecols'] = self.usecols
       1707 
    -> 1708         self._reader = parsers.TextReader(src, **kwds)
       1709 
       1710         passed_names = self.names is None
    

    pandas\_libs\parsers.pyx in pandas._libs.parsers.TextReader.__cinit__()
    

    pandas\_libs\parsers.pyx in pandas._libs.parsers.TextReader._setup_parser_source()
    

    FileNotFoundError: File b'Family_PACT_Providers_File.csv' does not exist

