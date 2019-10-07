# About the:   fpPropTaxData.json    File
This file contains public property tax data for properties in Forest Park, IL.

### Json File Format:
```
{
  dataSetTitle: "Cook County Property Tax Data For Forest Park, IL",
  scriptVersion: "1.0.1",
  notes: [array of strings of my comments about the data],
  githubRepo: "https://github.com/OrvilleChomer/OpenFP",
  githubFilePath: "https://github.com/OrvilleChomer/OpenFP/generatedDataFiles/fpPropTaxData.json",
  githubRawFilePath: "https://raw.githubusercontent.com/OrvilleChomer/OpenFP/master/generatedDataFiles/fpPropTaxData.json",
  pinData:[array of valid property data objects],
  missingPins:[array of objects for PINs not found on Cook County site],  
  pinsWithErrors:[array of objects where some sort of error occurred whilst trying to retrieve data],
  wrongPins:[array of objects for PIN that had data but were for a town other than Forest Park],
  retrievalStartTimestamp:{Date value of when the index.js script started},
  retrievalEndTimestamp:{Date value of when the index.js script completed}  
}
```

### Json Format for Property Data Object in the pinData Property's Array
```
{
   pin: "15-24-403-027-0000",
   searchStatus: "pin found",
   address: "",
   taxYrInfoAssVal: 12345,
   propAssVal: 12345,
   propEstVal: 12345,
   lotSz: 1000,
   bldingSz: 800,
   propCls: "",
   propTxRt: 12345,
   propTxCd: ""
}
```
| Object Property | Data Type | Description |
| --- | --- | --- |
| pin | string | Unique Identifier Cook County has for a property |
| searchStatus | string | valid values: 'pin found', 'pin not found', and 'error' |
| address | string | The street address of the property |
| taxYrInfoAssVal | numeric | Tax Year Assessed Value |
| propAssVal | numeric | Property Assessed Value |
| propEstVal | numeric | Property Estimated Value |
