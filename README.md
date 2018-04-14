# Shopify-RelatedItems
This is a tutorial to code creating a dynamic related items section for Shopify product pages. 

This section will dynamically pull items based on a metafield value and then sort them based on their product type. 

---
### Because this project utilizes the use of metafields, you or your client will need a way to edit them. Here are three of my favorite apps that allow editing of metafields:

MetaFields Editor:
https://apps.shopify.com/metafields-editor

Bulk Import Export Update with Excel:
https://apps.shopify.com/excel-export-import

Accentuate Custom Fields:
https://apps.shopify.com/accentuate

---

You will find the completed code for this tutoial in RelatedItems.liquid

> In my use case and this tutorial all products have a metafield value of "collection" that corrispond to the product collection they belong to. This is for the collections that each vendor has their products in such a a clothing company having a spring collection with similar looking clothes. This is not the same as a shopify collection.

1) This code will fit entirely in a single shopify section, create a new sectino and name it RelatedItems.
2) To begin, we need to make sure that this section only appears on products that have related items, so we will open and close an unless to check if the metafield we created to keep our collection is blank.
```
{%- unless product.metafields.global.collection == blank -%}
    <section id="RelatedProducts">
      <!-- This is where our content will live -->
    </section>
{%- endunless -%}
```
