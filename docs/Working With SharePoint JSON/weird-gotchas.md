# Weird Gotchas

## **Lists have two filters**

1. The first is visable in the list/gallery view. If you click a header you can filter on that column.
2. The second is only found when looking at the back end. You have to:
    1. Click on the view selection drop-down
    2. Select "Edit current view"
    3. The page that loads should have a heading of "Settings > Edit View"
    4. Scroll down to the "Filter" section, and modify/remove the filter as needed.

> This one was found by inadvertently toggling the second filter method. The list would only show a single entry, no matter what I did. I was only able to resolve this when I found this second filter method. I switched it back to "Show all items in this view."

## **Field names lie to you**

Yep. SharePoint lies to you. Don't act suprised.

JSON must use the _Internal Field Name_. This is **NEVER** updated after the column is created.

> If you create the columen and call it "Jobs" but decide you would rather call it "Desired Occupation" the _internal field name_ will still be "Jobs".

There is not an easy way to find the _internal field name_ of a column, go figure.

The best way is the following:

1. Click on the gear icon in the top right corner.
2. Click on `List settings`.
3. Scroll to the "Columns" section.
4. Click on the column you want to check.
5. The _internal field name_ is at the end of the URL in the address bar.

    > It will say `List=<long string>&Field=<internal field name>`

6. You can the use the _internal field name_ in JSON formatting as such: `"=[$<internal field name>]"`. If your fieldname is: `Desired_x0020_Occupation` you would use: `"=[$Desired_x0020_Occupation]"` to refer to that field in JSON formatting.

If you wanted the output to read: `Desired Occupation: <desired occupation>` you would use: `"='Desired Occupation: '+[$Desired_x0020_Occupation]"` for the `txtContent` attribute of the element.

## **If you use the SharePoint Buttons read this!**

If you use a SharePoint button to access things like the edit element panel (the slideout panel for editing an entry), then you need to do some manual additions to the JSON output from the formatter tool.

The JSON button element needs an attribute called `customRowAction`. This is not an HTML attribute, but a SharePoint attribute. This means you cannot specify this via HTML+CSS, and it will not populate into the JSON output. _You must add it manually._ Great! So much fun! Manual additions to automated workflows are the best!

```json
"customRowAction": {
    "action": "defaultClick"
},
```

Reference the syntax docs for the list of possible `action` values. The `defaultClick` action will open the edit panel, which suffices for us.
