# VBA Script Info For Script in Excel Workbook


This script takes an **Address_Points.kml** file (which I downloaded from Cook County web site) and uses it to generate a file (*fppoints.js*) containing JavaScript code for all the Property PIN numbers in Forest Park.

### Why did I Pick VBA?
There are plenty of ways that I'm sure I could have picked to read through this KML file, including Node.js. But a lot of these platforms are relatively new to me and I knew how to use Visual Basic read through a text file and parse it extremely well. And I wanted to get this working as quickly as possible. So, whether it was a good or bad decision, that is what I did!

### About the Script:
The input file is in an XML file format. Since I didn't know offhand what object library to use to read the XML *as* XML (being impatient), I just did a quick and dirty bit of code to open the input file as a text file, read in each line, search for a tag attribue of "PIN", and get its value. I then output a line for each PIN it finds to a line of JavaScript to push the PIN value to a JavaScript array. All these lines are wrapped in a JS function declaration for the function: **setupPins()**.

The idea is, that when this script is done running, and has created the *fppoint.js* file, I could open it up in a text editor, Select All, copy it to the Clipboard, then open up **index.js** in a text editor and Paste it at the end.

I decided to paste it at the *end* due to the large content size of the *fppoint.js* file so I would not have to scroll-scroll-scroll to get to the actual code that did the web/screen scraping!

*(Actual VBA Code extracted out of the Excel Workbook Below:)*
```
Public Sub genList()
    On Error GoTo TrapError
    
    Dim Q
    Dim sSearch
    Dim sLine
    Dim nPos
    Dim sVal
    Dim sOut
    
    ChDir "Main Hard Drive:Users:orvillechomer:Downloads"
    Open "Address_Points.kml" For Input As #1
    Open "fppoints.js" For Output As #2
    
    Q = Chr$(34)
    sSearch = "name=" & Q & "PIN" & Q
    
    Print #2, "function setupPins() {"
    
    While Not EOF(1)
        Line Input #1, sLine
        
        If InStr(sLine, sSearch) > 0 Then
            nPos = InStr(sLine, ">")
            sVal = Mid$(sLine, nPos + 1)
            nPos = InStr(sVal, "<")
            
            If nPos > 1 Then
                sVal = Mid$(sVal, 1, nPos - 1)
                sOut = "    pins.push(['" & Mid$(sVal, 1, 2) & "','" & Mid$(sVal, 3, 2) & "','" & Mid$(sVal, 5, 3) & "','" & Mid$(sVal, 8, 3)
                
                If Mid$(sVal, 11, 4) <> "0000" Then
                    sOut = sOut & "','" & Mid$(sVal, 11, 4)
                End If
                
                sOut = sOut & "']);"
                Print #2, sOut
                
            End If
            
            
        End If
        
    Wend
    
    Print #2, "} // end of function"
    
    
    Close #1
    Close #2
    MsgBox ("Done")
    
    Exit Sub
    
TrapError:
    MsgBox Err.Description
    Stop
    Resume
    
End Sub
```
Note the **ChDir** line above's path. It looks like this because I was running this script on a Mac and not a PC.
