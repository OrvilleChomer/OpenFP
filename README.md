# Scripts and Data for OpenFP Group
This is data from scripts I've created (and the scripts themselves) for the *Open FP Group* in Forest Park, IL.

Right now, I have a web scraping script to glean public property tax data for Forest Park from: http://cookcountypropertyinfo.com/default.aspx and save it to a json file.

You can find the latest copy of the json file: [here](https://github.com/OrvilleChomer/OpenFP/blob/master/generatedDataFiles/fpPropTaxData.json)

It is written in **Node.js** using Google's *Puppeteer*.


### Features that I still want to add to this script:

- Collect yearly tax billed amounts & tax history
- Collect yearly exemption information (seems to be just if there is an exemption or not)
- Collect yearly appeals information (seems to be just if there were appeals or not)
- Collect documents, deeds & liens information
