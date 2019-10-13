# VBA Script Info For Script in Excel Workbook


This script takes an **Address_Points.kml** file (which I downloaded from Cook County web site) and uses it to generate a file (*fppoints.js*) containing JavaScript code for all the Property PIN numbers in Forest Park.

The input file is in an XML file format. Since I didn't know offhand what object library to use to read the XML *as* XML (being impatient), I just did a quick and dirty bit of code to open the input file as a text file, read in each line, search for a tag attribue of "PIN", and get its value. I then output a line for each PIN it finds to a line of JavaScript to push the PIN value to a JavaScript array. All these lines are wrapped in a JS function declaration for the function: **setupPins()**.

The idea is, that when this script is done running, and has created the *fppoint.js* file, I could open it up in a text editor, Select All, copy it to the Clipboard, then open up xxxx.js in a text editor and Paste it at the end.

I decided to past it at the end due to the large content size of the *fppoint.js* file so I would not have to scroll-scroll-scroll to get to the actual code that did the web/screen scraping!

*(Actual VBA Code extracted out of the Excel Workbook)*
