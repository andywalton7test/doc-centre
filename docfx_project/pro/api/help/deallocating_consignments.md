# Deallocating Consignments

Change of plans for a consignment? This page explains how to deallocate consignments from their carrier services both individually and in bulk.

---

## Overview

A consignment cannot be edited once it is allocated. In order to edit or cancel an allocated consignment, or to allocate it to a different carrier service, you will first need to deallocate it.

> <span class="note-header">More Information:</span>
>
> For more information on editing existing consignments, see the <a href="/api/help/updating_existing_consignments.md"> Updating Existing Consignments</a> page.

Deallocating a consignment erases any allocation data that consignment holds and changes its state to _Unallocated_. You can only deallocate consignments that are in a state of _Allocated_, _Manifested_, or _Manifest Failed_.

## Deallocating Individual Consignments

The **Deallocate Consignment** endpoint enables you to deallocate a single consignment. To call **Deallocate Consignment**, send a `PUT` request to `https://api.electioapp.com/consignments/{consignmentReference}/deallocate`, where `{consignmentReference}` corresponds to the consignment that you want to deallocate. 

Once the request is received, PRO deallocates the consignment and returns a code _200_ response with no body. 

## Deallocate Multiple Consignments

The **Deallocate Consignments** endpoint enables you to deallocate multiple consignments in a single operation. To call **Deallocate Consignments**, send a `PUT` request to `https://api.electioapp.com/consignments/deallocatelist`. The body of the request should contain an array listing the `{consignmentReference}`s of the consignments that you want to deallocate.

Once the request is received, PRO deallocates each of the listed consignments in turn and returns an array listing the results of each deallocation attempt.  

### Deallocate Consignments Example

This examples shows a request to deallocate three consignments.

<div class="tab">
    <button class="staticTabButton">Example Deallocate Consignments Request</button>
    <div class="copybutton" onclick="CopyToClipboard(this, 'deallocateConsignmentsRequest')"><span class='glyphicon glyphicon-copy'></span><span class='copy'>Copy</span></div>
</div>

<div id="deallocateConsignmentsRequest" class="staticTabContent" onclick="CopyToClipboard(this, 'deallocateConsignmentsRequest')">

```json
[
    "EC-000-05D-EP2",
    "EC-000-05D-ENQ",
    "EC-000-05D-ENG"
]  
```

</div> 

<div class="tab">
    <button class="staticTabButton">Example Deallocate Consignments Response</button>
    <div class="copybutton" onclick="CopyToClipboard(this, 'deallocateConsignmentsResponse')"><span class='glyphicon glyphicon-copy'></span><span class='copy'>Copy</span></div>
</div>

<div id="deallocateConsignmentsResponse" class="staticTabContent" onclick="CopyToClipboard(this, 'deallocateConsignmentsResponse')">

```json
[
    {
        "IsSuccess": true,
        "Message": "Consignment deallocation completed successfully",
        "Data": "EC-000-05D-EP2",
        "ApiLinks": null
    },
    {
        "IsSuccess": true,
        "Message": "Consignment deallocation completed successfully",
        "Data": "EC-000-05D-ENQ",
        "ApiLinks": null
    },
    {
        "IsSuccess": true,
        "Message": "Consignment deallocation completed successfully",
        "Data": "EC-000-05D-ENG",
        "ApiLinks": null
    }
]
```

</div> 

## Next Steps

* Learn about alternative methods of allocating consignments at the [Allocating Consignments](/api/help/allocating_consignments.html) page.
* Learn how to get and print delivery labels at the [Getting Labels](/api/help/getting_labels.html) page.
* Learn how to add consignments to a carrier manifest at the [Manifesting Consignments](/api/help/manifesting_consignments.html) page.

<script src="../../scripts/requesttabs.js"></script>
<script src="../../scripts/responsetabs.js"></script>
<script src="../../scripts/copy.js"></script>