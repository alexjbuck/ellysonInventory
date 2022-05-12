# General Settings for Lists

To get to the general settings for a list

1) Click the List View button in the ribbon
2) Click the "Edit current view" button

## General Settings

This is where you can control all the settings for a list.
You can adjust column definitions here, as well as view options.

## Hiding Title column

Reference this resource <https://www.enjoysharepoint.com/remove-sharepoint-online-title-column/>.

In short, go to Settings > Advanced Settings > "Allow management of content types?" and set it to "Yes".

Then go back to Settings. There is a new section called "Content Type". Click the text `Item`. Then click the `Title` entry on the new page. This will finally load a page that has an option called "Column Settings" where one option is "Hidden (Will not appear in forms)". Select this and press "OK".

Once you have done this, go back to Settings > Advanced Settings > "Allow management of content types?" and set it to "No". If you do not, there is a "Content Type" field that now will show up on forms. Lovely.

## Multi-line Text and "Rich Text Fields"

Don't use Rich Text Fields.

Just don't.

If you use "rich text" fields, when you get the contents of the field you get a bunch of HTML tags that do not render, but instead just print out raw.

    Multi-line Description: <div>Rich text field contents</div>

Looks bad.
