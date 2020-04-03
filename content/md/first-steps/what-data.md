---
id: what-data
themes: first-steps
title: What PIM data are imported into SFCC?
popular: false
related: trigger, overview
---

# Attribute types

The Akeneo Connector imports the following PIM attribute types to SFCC:


- Text
- Text area
- Date
- Number
- Simple select (1)
- Multiple select (1)
- Yes/No
- Metric (2)
- Image
- File (3)
- Asset collection (EE) (4)
- Price (5)
- Identifier
- Table attribute (6)

::: info
(1) The connector imports all **attribute options** with their translations.<br>

(2) As **metric attributes** do not exist in SFCC, the connector converts them into **text attributes**.<br>

(3) As SFCC does not support the import of binary files other than images, the connector only imports **the relative PIM path** for this type of attributes.<br>

(4) As SFCC does not support the import of binary files other than images, the connector only imports **image assets binaries**.<br>

(5) As Akeneo PIM should only manage "cold" information, your product **price** as well as **stock** information should not be retrieved by the cartridge. You need a "direct" connection between your ERP and your SFCC for that. The PIM **price** attribute is only for the "reference price" of your product.  

(6) `Table attributes` do not exist by default in the PIM. This attribute type has been developed as an add-on by our Solution Partner [Flagbit](https://marketplace.akeneo.com/extension/table-attribute), and the [Webkul](https://marketplace.akeneo.com/extension/akeneo-table-attribute) company.
**Please note that the Akeneo Connector for SFCC is compatible with any of these add-ons**.
As SFCC does not have a table attribute type, the connector imports table data into an SFCC **text area** attribute as a **JSON structure**.  
:::


# Attributes

The Akeneo Connector for SFCC imports all your PIM products attributes to Salesforce Commerce Cloud.

If you have some **localizable** attributes (attributes that can have different values per **locale**): the Akeneo Connector will import the content of these attributes in the different languages of an SFCC product.

If you have some **scopable** attributes (attributes that can have different values per **channel**): depending on your [channel configuration](03-products-filter-configuration.html), the Akeneo Connector will import the attribute values of the defined channel.

# Categories

Depending on your [category configuration](06-categories-configuration.html), Akeneo Connector for SFCC can import all PIM category trees.

::: info
**Mapping between Akeneo PIM and SFCC:**<br>
The Akeneo Connector for SFCC maps PIM categories with SFCC categories.<br>
Because your **PIM categories** has only one title while **SFCC categories** have more information (description, image, etc.), Akeneo Connector for SFCC will only import the PIM category title information to SFCC.
:::

# Products, Product models

Depending on your [product filter configuration](03-products-filter-configuration.html), Akeneo Connector for SFCC will import products and product models of your PIM catalog.

::: info
**Mapping between Akeneo PIM and SFCC:**<br>
Akeneo Connector for SFCC maps PIM products with SFCC `products`.
:::

::: info
**Mapping between Akeneo PIM and SFCC:**<br>
Akeneo Connector for SFCC maps PIM product models this way:

**PIM Product models with 1 level of variation:**<br>
- PIM product models `common` part with SFCC `Variation master`<br>
- PIM product models variation `level 1` part with SFCC `Variation products`

**PIM Product models with 2 level of variation:**<br>
- PIM product models `common` part with SFCC `Variation master`<br>
- PIM product models variation `level 1`+ variation `level 2` parts with SFCC `Variation products`

Alternative: since the version **v19.6.0** of the SFCC Connector, you can model PIM Product model with 2 levels of variation like this:
- PIM product models `common` part is mapped with SFCC `Variation master`
- PIM product models variation `level 1` part is mapped with SFCC `Variation group`
- PIM product models variation `level 2` part is mapped with SFCC `Variation products`
:::

# Product associations

Depending on your [product association mapping configuration](05-mapping-configuration.html), Akeneo Connector for SFCC will import your PIM product associations.

**Mapping between your PIM and SFCC:**<br>
Akeneo Connector for SFCC maps PIM `product associations` with SFCC `product recommendations`.<br>
Depending on your [product association mapping configuration](05-mapping-configuration.html), each PIM `product association type` will be mapped with SFCC `product recommendation type`.

::: info
** Since the Akeneo Connector for SFCC V19.3.3 **
Akeneo Connector for SFCC can also map PIM `product associations` with SFCC `product links`.<br>
Depending on your [product association mapping configuration](05-mapping-configuration.html), each PIM `product association type` will be mapped with SFCC `product link type`.
:::

# Currencies

The Akeneo Connector for SFCC also imports all your PIM currencies.

::: info
**Mapping between Akeneo PIM and SFCC:**<br>
Akeneo Connector for SFCC maps PIM `currencies` with SFCC `Pricebook`.
:::

# Product groups

::: warning
As there is no such thing as Product Groups in SFCC, the connector does not import PIM product groups yet.
:::

# Reference Entities [EE] [3.x]

Since the Akeneo Connector for SFCC `V19.8.0`, the Connector can manage PIM Reference Entity Records.

Depending on your [Reference entity configuration](08-reference-entities.html), PIM `Reference Entity Records` will be mapped with SFCC `Content assets`.
