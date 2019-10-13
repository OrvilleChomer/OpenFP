# Scripts and Data for OpenFP Group
This is data from scripts I've created (and the scripts themselves) for the *Open FP Group* in Forest Park, IL.

Right now, I have a web scraping script to glean public property tax data for Forest Park from: http://cookcountypropertyinfo.com/default.aspx and save it to a json file.

You can find the latest copy of the json file: [here](https://github.com/OrvilleChomer/OpenFP/blob/master/generatedDataFiles/fpPropTaxData.json)

It is written in **Node.js** using Google's *Puppeteer*.

### Where Did I get the Propery PIN Numbers From?
I manually went to [this page](https://hub-cookcountyil.opendata.arcgis.com/datasets/5ec856ded93e4f85b3f6e1bc027a2472_0/data). This provides reporting for *Address Points* in Cook County.
- To begin with, the dataset will have approx 1,340,255 total rows.
- Scroll horizontally over to the **Zip Code** column. 
- There will be an icon next to it that looks like a little funnel... click it.
- A new button that is labeled **Zip Code** will appear above the report. click that button.
- A dropdown containing a text box will appear underneath this button. For *Forest Park* enter **60130** and press the *return* key.
- You will wait a few moments and the grid will refresh with Forest Park items only.
- The dataset will now show a total count of approx: 3,380 rows.  Much smaller!
- On the right side of the report is a *Download* button.  Click it.
- A dropdown will appear. One of the options is: **KML**   Pick that option.
- You may be prompted if you want to download the data. If you are, click the *Allow* button.
- The data file will download.
- Copy the file to the destination where a script is expecting to use it.

### Features that I still want to add to this script to collect some historical information:

- Collect yearly tax billed amounts & tax history
- Collect yearly exemption information (seems to be just if there is an exemption or not)
- Collect yearly appeals information (seems to be just if there were appeals or not)
- Collect documents, deeds & liens information
- Output this data into a mySQL database file.
- Output this data into an NeDb (subset of Mongo Db) database file.
