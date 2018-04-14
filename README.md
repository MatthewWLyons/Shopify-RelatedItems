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

This code will fit entirely in a single shopify section, create a new sectino and name it RelatedItems.

In order for this code to work there must be a shopify collection created with a name that matches exactly what the product has in the metafield, for this I recommend tagging the product with the same value as the metafield and then having a smart collection with the same name look for products tagged with that value. 

### 1) To begin, we need to make sure that this section only appears on products that have related items, so we will open and close an unless to check if the metafield we created to keep our collection is blank.
```
{%- unless product.metafields.global.collection == blank -%}
    <section id="RelatedProducts">
      <!-- This is where our content will live -->
    </section>
{%- endunless -%}
```
### 2) Now in order to make sure we only grab the items in the same collection we need to pass the mtafield value into a for product statement:
```
{%- unless product.metafields.global.collection == blank -%}
    <section id="RelatedProducts">
        {%- for product in collections[product.metafields.global.collection].products -%}
        <a href="{{ product.url }}">
            <h1>{{ product.name }}</h1>
        </a>
        {%- endfor -%}
    </section>
{%- endunless -%}
```
Notice the `collections[product.metafields.global.Related].products` in the for loop. You can pass any metafield or other liquid code as a variable into another section of liquid code using square brackets.

>Note: When passing a variable into other liquid code leave out the first period and make the object plural:

```collections[product.metafields.global.Related].products```

>Not:

```collection.[product.metafields.global.Related].products```

This will select products in the collection that corrisponds to the value of the metafield. If you are using this right, you should have an output of each product in the collection with a link to their product page
