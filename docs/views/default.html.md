```html
<div class="outer">
    <div class="title">
=[$Title]
    </div>
    <div class="objective">
    <div class="label">=if([$ProjectObjective],'Project Objective:','')</div>
        <div>
=[$ProjectObjective]
        </div> 
    </div>
    <div class="poc">
        <span class="label">Point of Contact: </span><a href="='mailto:'+[$Email]">=[$Point_x0020_of_x0020_Contact_x00]</a>
    </div>
    <div class="poc">
        <span class="label">=if([$SecondaryPOCName],'Secondary Point of Contact: ','')</span><a href="='mailto:'+[$SecondaryPOCEmail]">=[$SecondaryPOCName]</a>
    </div>
    <div class="status">
        <span class="label">=if([$ProjectStatus],'Project Status: ','')</span><span class="emphasis">=[$ProjectStatus]</span>
    </div>
    <div class="start">
        <span class="label">=if([$StartDate],'Project Start: ','')</span><span class="emphasis">=toLocaleDateString([$StartDate])</span>
    </div>
    <div class="end">
        <span class="label">=if([$EndDate],'Project End: ','')</span><span class="emphasis">=toLocaleDateString([$EndDate])</span>
    </div>
    <div class="sponsor clear">
        <span class="label">=if([$PrimaryPMA],'Primary PMA: ','')</span><span class="emphasis">=[$PrimaryPMA]</span>
    </div>
    <a href="='https://flankspeed.sharepoint-mil.us.mcas-gov.us/sites/navair_autonomy_and_ai_coi/Lists/AI%20Project%20Inventory/DetailView.aspx?useFiltersInViewXml=1&FilterField1=ID&FilterValue1='+[$ID]">
        <div class="btn">
            View Project
        </div>
    </a>
    <button class="sp-btn">
        <div class="btn">
            Edit Project
        </div>
    </button>
</div>
```
