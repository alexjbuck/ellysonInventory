# How to filter a list to a single item via URL query string

Filtering is accomplished by adding a query string to the URL.

For this we will assume that `<url>` is a valid url to the list/view you want to filter.

e.g.

    https://flankspeed.sharepoint-mil.us.mcas-gov.us/sites/navair_autonomy_and_ai_coi/Lists/AI%20Project%20Inventory/DefaultFormatted.aspx

The format to use for applying a filter is:

    <url>?FilterField1=<field-name>&FilterValue1=<field-value>

e.g.

    https://flankspeed.sharepoint-mil.us.mcas-gov.us/sites/navair_autonomy_and_ai_coi/Lists/AI%20Project%20Inventory/DefaultFormatted.aspx?FilterField1=ID&FilterValue1=1
