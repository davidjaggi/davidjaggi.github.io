The following code extracts data directly from MultiCharts. Create an indicator and insert the following code:

```
Inputs: 
  iPrint(False),
  iFileName("C:\Users\Administrator\5min.txt"),
  iPrecision(4);
  
Variables:
  dateInDateTimeFormat(0), 
  timeInDateTimeFormat(0),
  dateReadable(""),
  timeReadable("");
  
Once begin
      Print(File(iFileName),"Date,Time,Open,High,Low,Close,Vol,OI" ); 
end ;
   
dateInDateTimeFormat = ElDateToDateTime(Date);
timeInDateTimeFormat = eltimetodatetime(Time);
dateReadable = FormatDate("MM/dd/yyyy",dateInDateTimeFormat);
timeReadable = FormatTime("HH:mm",timeInDateTimeFormat);
if iPrint = True then
  Print(File(iFileName),dateReadable + "," + timeReadable + "," + NumToStr(O,iPrecision) + ","+
    NumToStr(H,iPrecision)+","+NumToStr(L,iPrecision)+","+NumToStr(C,iPrecision)+","+
    NumToStr(Volume,0)+","+NumToStr(OpenInt,0));

```

Adjust the iFilename and set it to the correct path where you want to store the txt-file. iPrecision lets you decide how many decimal places the exported file should contain. The headings are “Date,Time,Open,High,Low,Close,Vol,OI” which are specially set in order to import the file into BuildAlpha. After inserting the indicator into MC set the bar time correctly and set the input iPrint to true. The file should only take a few seconds to be generated.