---
title: Cells
seo-title: Cells
description: Cells
seo-description: 
page-status-flag: never-activated
uuid: 8be8d7a5-44d2-45ee-af0d-6e05db7fe440
contentOwner: sauviat
topic-tags: targeting-activities
products: SG_CAMPAIGN/CLASSIC
content-type: reference
discoiquuid: a5219f25-b5ff-42fd-b07d-11f3f4ab7453
index: y
internal: n
snippet: y
---

# Cells{#cells}

The **Cells** activity provides a view of the various subsets in the form of data columns. It facilitates subset manipulation and is also designed to encourage personalization possibilities.

![](assets/wf_split_cells.png)

This activity can be configured to enter specific parameters based on user needs. By default, the detail of each subset is detailed in a dedicated window via the **Selection** and **Advanced** tabs. In the example below, the form has been modified: a **Data** tab has been added to enable the association of an offer and a priority level for each subset.

![](assets/wf_split_cells_with_customization.png)

For this configuration, the following information was added to the workflow form (in the **Administration > Configurations > Input forms** node of the Adobe Campaign tree):

```
<container img="nms:miniatures/mini-enrich.png" label="Data">
                <input xpath="@code"/>
                <container xpath="select/node[@alias='@numTest']">
                  <input alwaysActive="true" expr="'long'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Priority'" type="expr" xpath="@label"/>
                  <input label="Priority" maxValue="12" minValue="0" type="number"
                         xpath="@value" xpathEditFromType="@type"/>
                </container>
                <container xpath="select/node[@alias='@test']">
                  <input alwaysActive="true" expr="'string'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'Identifier'" type="expr" xpath="@label"/>
                  <input label="Cell identifier" xpath="@value"/>
                </container>
                <container xpath="select/node[@alias='linkTest']">
                  <input alwaysActive="true" expr="'link'" type="expr" xpath="@type"/>
                  <input alwaysActive="true" expr="'nms:offer'" type="expr" xpath="@dataType"/>
                  <input alwaysActive="true" expr="'Offre'" type="expr" xpath="@label"/>
                  <input computeStringAlias="@valueLabel" label="Offers" notifyPathList="@_cs|@valueLabel"
                         schema="nms:offer" type="linkEdit" xpath="@value"/>
                </container>
```

Entry form personalization in Adobe Campaign is reserved for expert users. For more on this, refer to this [section](../../configuration/using/identifying-a-form.md).