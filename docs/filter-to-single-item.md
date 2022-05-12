# How to filter a list to a single item via URL query string

Filtering is accomplished by adding a query string to the URL.

For this we will assume that `<url>` is a valid url to the list/view you want to filter.

e.g.

    https://flankspeed.sharepoint-mil.us.mcas-gov.us/sites/navair_autonomy_and_ai_coi/Lists/AI%20Project%20Inventory/DefaultFormatted.aspx

The format to use for applying a filter is:

    <url>?FilterField1=<field-name>&FilterField2=<field-value>

e.g.

    https://flankspeed.sharepoint-mil.us.mcas-gov.us/sites/navair_autonomy_and_ai_coi/Lists/AI%20Project%20Inventory/DefaultFormatted.aspx?FilterField1=Title&FilterValue1=Adaptive%20Learning%20for%20Stall%20Pre%2Dcursor%20Identification%20and%20General%20Impending%20Failure%20Prediction
