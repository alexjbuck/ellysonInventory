# Importing data from STAIRS exports

First off. Sorry, this is NOT going to be enjoyable.

It would be cool if the "Upload from Excel" option from Sharepiont worked, or the "Export Table to Sharepoint List" option from Excel worked, or even the fallback of "copy paste the cells into grid view" worked. None of them work out of the gate. 

1. Upload from Excel requires "Add an App" to the sharepoint site. When you try this in Flankspeed, it says there are no Sharepoint Apps that you can add. Bummer.
2. Export table to sharepoint list sounded promising, Excel can make connections to OneDrive, why not SharePoint? "Cannot contact the server at this time. Your table cannot be published."
3. Copy paste cells into grid view works, _sorta_. Tab characters (ASCII 09) split the contents into the next column, so your data does not paste in nicely.

## What can we do

Well, there's really we can do about 1 or 2. Maybe somebody on the licensing side (I say that as if its a concrete thing or person, who knows), can fix that one day.

What we _can_ do is work with 3 and try to clean the CSV up before running the copy/paste into Sharepoint. We need to find and replace all tab characters (ASCII 09) with an empty string "". Excel has a find/replace but there is no good way to put in a tab character. You cannot copy/paste the tab character (they don't render in Excel). In my despair, I fell back on the reliable solution for finding and subsituting text, **sed**.

## sed, the tool you hate to love

If you don't use \*nix based OS's you might not have heard of sed. sed does **many** things, but one thing it does very well is text substitution. sed, or <ins>s</ins>tream <ins>ed</ins>itor, is a super powerful tool for editing/replacing text.

The command uses a text pattern string to determine what to find/replace, and it is, admittably, rather arcane to the uninitiated. Don't worry though, the command to find and replace all tabs is fairly simple

```shell
's/\t//g'
```

the full command (if you had sed installed local)
```shell
sed 's/\t//g' file.csv
```

sed is not installed on windows machines, however, there is a webapp that you can use to run [sed](https://sed.js.org/).

1. Open the CSV in a text editor.
2. Copy all the text and paste it into the input labelled STDIN
3. Copy and paste the string `'s/\t//g'` into the input labelled Command Line.
4. Paste the STDOUT text back into the text file and save as CSV.
5. Reopen the CSV in excel.
6. Copy all the cells
7. On Sharepoint, select all columns in the new-item row
8. Paste, all items should appear.

