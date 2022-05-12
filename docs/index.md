# Getting Started

Okay, This is a pretty disorganized set of notes at this point. Check the navigation bar for the "Working With SharePoint JSON" section.

The general idea of the project is to create a tool that lets us visualize the **People** and **Projects** that we have in our organization.

We discussed two views for projects, one that is a **Overview** and one that is a **Detail**. Right now these are called `DefaultFormatted` and `DetailView` respectively.

## Projects 

Projects have the fields from the STAIRS system. Most of these fields are not rendered in the UI as it is written, however. The overview shows the following fields (_if they exist_):

- Title
- Point of Contact (as a mailto:link)
- Secondary Point of Contact (as a mailto:link)
- Project Status (this maybe can go away, I'm not sure that the STAIRS project status field is relevant. Or we can move the STAIRS project status field to a STAIRS-project status and implement our own Project Status field.)
- Project Start Date
- Project End Date
- Project Description

There is a button on each project that takes you to the detail view. You can manually switch views to the Detailed view, but it will not be filtered down to a single project. The button will change views _and_ filter down to the single project.

The Detail view adds in the Project Description field, which tends to be very long. I actually had to delete some of the description entries from the STAIRS export because weird formatting issues. 

> Certain control characters were causing the single cell to paste into multiple cells when migrating the Excel data into SharePoint. Unfortunately, I couldn't figure out how to fix this. I also could not create the list _from_ the Excel data; this is supposed to be an option per the documentation, but it was not an available option to me.


## People

People are represented by a SharePoint person object and tags for their interests. 

## Project-People Relationships

I have implemented the basic list for this, which uses a lookup field on project titles and a person object to select the person. 

I have concluded there is no _organic SharePoint_ way to implement the many-to-many relationship mapping with the People and Project lists.
My current guess is that you can implement this with a PowerAutomate flow that runs whenever the Project-People join list is updated. 

1. Get the list of relationships.
2. For each relationship:
    1.  check if the project exists. (It should, the lookup field is configured to have referential integretiy and delete the relationship if the project is deleted.)
    2. If the project exists, check if the person exists. (People objects cannot be targets of lookup fields {because of course... :facepalm:}, so we have no guarantee that the person exists, i.e. no referential integrity.)
    3. If the person exists, go into the project list and append the person to the "Interested People" field.
    4. If the person exists, go into the person list and append the project to the "Interested Projects" field.
    5. If the person does not exists, delete the relationship entry.

I have not implemented _ANY_ of the PowerAutomate flow for this yet.

## Forms

The SharePoint default form includes _every_ field. This works for now, maybe isn't idea. Unfortunately you have to use PowerAutomate to customize these forms. PowerAutomate is _NOT_ accessible from a non-NMCI connection, again, because why would it be? I was working well on my home computer and really did not want to pull out my work laptop...

The general idea is to use what I did when demonstrating PowerAutomate update emails. This creates a link to an edit form for just the one project entry.

## Permissions

I don't know anything about this yet. We'll need to lock things down *somewhat* to prevent people from messing with the data. 

## References and Quicklinks

Below are a few quick links to get you started.

[FRAG JSON Test site](https://flankspeed.sharepoint-mil.us.mcas-gov.us/sites/CPF-CNAF-FRAG/Lists/jTestJSONlist/jTestJSON2.aspx)

[AI Project List](https://flankspeed.sharepoint-mil.us.mcas-gov.us/sites/navair_autonomy_and_ai_coi/Lists/AI%20Project%20Inventory/AllItems.aspx)

[AI Person List](https://flankspeed.sharepoint-mil.us.mcas-gov.us/sites/navair_autonomy_and_ai_coi/Lists/AI%20Person%20Inventory/AllItems.aspx)

[Person Project Join List (Experimental)](https://flankspeed.sharepoint-mil.us.mcas-gov.us/sites/navair_autonomy_and_ai_coi/Lists/AI%20Person%20Project%20Join/AllItems.aspx)

[JSON Formatter](https://pnp.github.io/List-Formatting/tools/html-formatter-generator/)

[List Format Syntax Reference](https://docs.microsoft.com/en-us/sharepoint/dev/declarative-customization/formatting-syntax-reference)
