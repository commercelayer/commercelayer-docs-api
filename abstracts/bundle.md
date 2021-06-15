Bundles describe a set of specific products that are being sold. A unique code identifies each bundle within the market. The bundle name, description, and image URL are best suited for internal usage (Commerce Layer is not a CMS).
Bundles are linked to manual SKU lists, inheriting the SKUs from there. A **maximum of 5 SKU list items** are permitted for each bundle.  
Once an SKU list is associated with a bundle, its items cannot be added, removed or updated, unless you first destroy all of the linked bundles.
Bundles have `price_amount_cents` and `compare_at_amount_cents` attributes: the latter can be specified or computed as the sum the SKUs, but is always guaranteed to be smaller or equal than the former.
