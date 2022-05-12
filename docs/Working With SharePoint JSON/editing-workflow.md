# JSON Editing Workflow

## Baseline JSON

The general workflow to build the starter JSON goes as follows:

1. Write HTML
2. Write CSS
3. Input HTML + CSS into [formatter](https://pnp.github.io/List-Formatting/tools/html-formatter-generator/)
4. Iterate until you like the output appearance

## JSON Tweaks

By default the tool builds _column_ syntax JSON. We're concerned with building _view_ syntax JSON entries.

The output will start with the following:

```json
{
"$schema": "https://developer.microsoft.com/json-schemas/sp/v2/column-formatting.schema.json",
"debugMode": true,
"elmType": "div",
...
}
```

You can see that this is the _column_ syntax JSON based on the schema.

What you need to do is take the output starting with `"elmType": "div"` (_Be careful to not grab the ending `}` from the top level of the output_) and add insert it into the following template:

```json
{
"$schema": "https://developer.microsoft.com/json-schemas/sp/view-formatting.schema.json",
"hideSelection": true,
"hideColumnHeader": true,
"rowFormatter": {
    <INSERT HERE>
    },
}
```

The result will look something like this:

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/sp/view-formatting.schema.json",
  "hideSelection": true,
  "hideColumnHeader": true,
  "rowFormatter": {
    "elmType": "div",
    "style": {
      "display": "flex",
    },
    "attributes": {
      "class": "ms-bgColor-white"
    },
    "children": [
        <YOUR CHILDREN ELEMENTS HERE>
    ]
  }
}
```

The specifics the element style, attributes, and children are up to you and your formatting. You may also modify the `hideSelection` and `hideColumnHeader` properties as desired.

## Highly recommend getting the skeleton correct first

There are a few items that you have to do _after_ you get the skeleton. If you use JSON button elements, you will need to add the `defaultRowAction` property in manually. This is described in [weird gotchas](weird-gotchas.md).
