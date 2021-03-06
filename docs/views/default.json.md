```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/sp/view-formatting.schema.json",
  "hideSelection": true,
  "hideColumnHeader": true,
  "rowFormatter": {

    "elmType": "div",
    "attributes": {
      "class": "outer"
    },
    "style": {
      "margin": "1em",
      "padding": "1em",
      "border": "1px solid #ccc",
      "background-color": "#eee",
      "display": "block",
      "box-shadow": "1px 1px 2px black",
      "border-radius": "5px"
    },
    "children": [
      {
        "elmType": "div",
        "attributes": {
          "class": "title"
        },
        "style": {
          "font-size": "1.2em",
          "text-align": "left",
          "font-weight": "bold"
        },
        "txtContent": "=[$Title]    "
      },
      {
        "elmType": "div",
        "attributes": {
          "class": "objective"
        },
        "children": [
          {
            "elmType": "div",
            "attributes": {
              "class": "label"
            },
            "style": {
              "color": "#333",
              "font-weight": "100"
            },
            "txtContent": "=if([$ProjectObjective],'Project Objective:','')"
          },
          {
            "elmType": "div",
            "txtContent": "=[$ProjectObjective]        "
          }
        ]
      },
      {
        "elmType": "div",
        "attributes": {
          "class": "poc"
        },
        "style": {
          "font-size": "1.2em"
        },
        "children": [
          {
            "elmType": "span",
            "attributes": {
              "class": "label"
            },
            "style": {
              "color": "#333",
              "font-weight": "100"
            },
            "txtContent": "Point of Contact: "
          },
          {
            "elmType": "a",
            "attributes": {
              "href": "='mailto:'+[$Email]"
            },
            "style": {
              "color": "teal"
            },
            "txtContent": "=[$Point_x0020_of_x0020_Contact_x00]"
          }
        ]
      },
      {
        "elmType": "div",
        "attributes": {
          "class": "poc"
        },
        "style": {
          "font-size": "1.2em"
        },
        "children": [
          {
            "elmType": "span",
            "attributes": {
              "class": "label"
            },
            "style": {
              "color": "#333",
              "font-weight": "100"
            },
            "txtContent": "=if([$SecondaryPOCName],'Secondary Point of Contact: ','')"
          },
          {
            "elmType": "a",
            "attributes": {
              "href": "='mailto:'+[$SecondaryPOCEmail]"
            },
            "style": {
              "color": "teal"
            },
            "txtContent": "=[$SecondaryPOCName]"
          }
        ]
      },
      {
        "elmType": "div",
        "attributes": {
          "class": "status"
        },
        "children": [
          {
            "elmType": "span",
            "attributes": {
              "class": "label"
            },
            "style": {
              "color": "#333",
              "font-weight": "100"
            },
            "txtContent": "=if([$ProjectStatus],'Project Status: ','')"
          },
          {
            "elmType": "span",
            "attributes": {
              "class": "emphasis"
            },
            "style": {
              "font-style": "italic"
            },
            "txtContent": "=[$ProjectStatus]"
          }
        ]
      },
      {
        "elmType": "div",
        "attributes": {
          "class": "start"
        },
        "style": {
          "float": "left"
        },
        "children": [
          {
            "elmType": "span",
            "attributes": {
              "class": "label"
            },
            "style": {
              "color": "#333",
              "font-weight": "100"
            },
            "txtContent": "=if([$StartDate],'Project Start: ','')"
          },
          {
            "elmType": "span",
            "attributes": {
              "class": "emphasis"
            },
            "style": {
              "font-style": "italic"
            },
            "txtContent": "=toLocaleDateString([$StartDate])"
          }
        ]
      },
      {
        "elmType": "div",
        "attributes": {
          "class": "end"
        },
        "style": {
          "float": "right"
        },
        "children": [
          {
            "elmType": "span",
            "attributes": {
              "class": "label"
            },
            "style": {
              "color": "#333",
              "font-weight": "100"
            },
            "txtContent": "=if([$EndDate],'Project End: ','')"
          },
          {
            "elmType": "span",
            "attributes": {
              "class": "emphasis"
            },
            "style": {
              "font-style": "italic"
            },
            "txtContent": "=toLocaleDateString([$EndDate])"
          }
        ]
      },
      {
        "elmType": "div",
        "attributes": {
          "class": "sponsor clear"
        },
        "style": {
          "clear": "both"
        },
        "children": [
          {
            "elmType": "span",
            "attributes": {
              "class": "label"
            },
            "style": {
              "color": "#333",
              "font-weight": "100"
            },
            "txtContent": "=if([$PrimaryPMA],'Primary PMA: ','')"
          },
          {
            "elmType": "span",
            "attributes": {
              "class": "emphasis"
            },
            "style": {
              "font-style": "italic"
            },
            "txtContent": "=[$PrimaryPMA]"
          }
        ]
      },
      {
        "elmType": "a",
        "attributes": {
          "href": "='https://flankspeed.sharepoint-mil.us.mcas-gov.us/sites/navair_autonomy_and_ai_coi/Lists/AI%20Project%20Inventory/DetailView.aspx?useFiltersInViewXml=1&FilterField1=ID&FilterValue1='+[$ID]"
        },
        "style": {
          "color": "teal"
        },
        "children": [
          {
            "elmType": "div",
            "attributes": {
              "class": "btn"
            },
            "style": {
              "-webkit-appearance": "button",
              "-moz-appearance": "button",
              "appearance": "button",
              "color": "#fff",
              "display": "inline-block",
              "padding": ".5em",
              "margin-top": "1em",
              "border": "1px solid #111",
              "border-radius": "3px",
              "cursor": "pointer",
              "background-color": "#004E8C",
              "box-shadow": "1px 1px 2px black"
            },
            "txtContent": "            View Project        "
          }
        ]
      },
      {
        "elmType": "button",
        "attributes": {
          "class": "sp-btn"
        },
        "customRowAction": {
          "action": "defaultClick"
        },      
        "style": {
          "border": "0",
          "font-size": "1em"
        },
        "children": [
          {
            "elmType": "div",
            "attributes": {
              "class": "btn"
            },
            "style": {
              "-webkit-appearance": "button",
              "-moz-appearance": "button",
              "appearance": "button",
              "color": "#fff",
              "display": "inline-block",
              "padding": ".5em",
              "margin-top": "1em",
              "border": "1px solid #111",
              "border-radius": "3px",
              "cursor": "pointer",
              "background-color": "#004E8C",
              "box-shadow": "1px 1px 2px black"
            },
            "txtContent": "            Edit Project        "
          }
        ]
      }
    ]

  }
}
```
