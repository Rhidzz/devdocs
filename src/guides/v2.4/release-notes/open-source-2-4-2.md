---
group: release-notes
title: Magento Open Source 2.4.2 Release Notes
---

Magento Open Source 2.4.2 introduces enhancements to performance and security plus significant platform improvements. Security enhancements include expansion of support for the `SameSite` attribute for all cookies. Elasticsearch 7.9.x and Redis 6.x are now supported.

This release includes over 280 new fixes to core code, and over 30 security enhancements. It includes the resolution of almost 290 GitHub issues by our community members. These community contributions range from minor clean-up of core code to significant enhancements in GraphQL.

All known issues identified in Magento 2.4.1 have been fixed in this release.

{:.bs-callout-info}

Quarterly releases may contain backward-incompatible changes (BIC). Magento 2.4.2 contains minor backward-incompatible changes. To review minor backward-incompatible changes, see [BIC reference]({{page.baseurl}}/release-notes/backward-incompatible-changes/reference.html). (Major backward-incompatible issues are described in [BIC highlights]({{page.baseurl}}/release-notes/backward-incompatible-changes/index.html). Not all releases introduce major BICs.)

## Security-only patch available

Merchants can now install time-sensitive security fixes without applying the hundreds of functional fixes and enhancements that a full quarterly release provides (for example, Magento 2.4.1-p1). Patch 2.4.0.12 (Composer package 2.4.1-p1) is a security-only patch that provides fixes for vulnerabilities that have been identified in our previous quarterly release, Magento 2.4.1. All hot fixes that were applied to the 2.4.1 release are included in this security-only patch. (A *hot fix* provides a fix to a released version of Magento that addresses a specific problem or bug.)

For general information about security-only patches, see the Magento DevBlog post [Introducing the New Security-only Patch Release](https://community.magento.com/t5/Magento-DevBlog/Introducing-the-New-Security-only-Patch-Release/ba-p/141287). For instructions on downloading and applying security-only patches (including patch 2.4.1-p1), see [Install Magento using Composer]({{ page.baseurl }}/install-gde/composer.html). Security-only patches include security bug fixes only, not the additional security enhancements that are included in the full patch.

## Other release information

Although code for these features is bundled with quarterly releases of the Magento core code, several of these projects (for example, Progressive Web Applications (PWA) Studio) are also released independently. Bug fixes for these projects are documented in the separate, project-specific release information that is available in the documentation for each project.

## Highlights

Look for the following highlights in this release.

### Substantial security enhancements

This release includes over 35 security fixes and platform security improvements. All security fixes have been backported to Magento 2.4.1-p1 and Magento 2.3.6-p1.

#### Over 35 security enhancements that help close remote code execution (RCE) and cross-site scripting (XSS) vulnerabilities

No confirmed attacks related to these issues have occurred to date. However, certain vulnerabilities can potentially be exploited to access customer information or take over administrator sessions. Most of these issues require that an attacker first obtains access to the Admin. As a result, we remind you to take all necessary steps to protect your Admin, including but not limited to these efforts: IP allowlisting, [two-factor authentication]({{page.baseurl}}/security/two-factor-authentication.html), use of a VPN, the use of a unique location rather than `/admin`, and good password hygiene.

#### Additional security enhancements

Security improvements for this release include:

*  All core cookies now support the `SameSite` attribute.

*  Magento now displays messages that identify potentially malicious content in product and category description fields when the user tries to save values in these fields.

*  File system operations across Magento components have been standardized and hardened to prevent malicious uploads.

*  Core Content Security Policy (CSP) violations have been fixed.

{:.bs-callout-info}
Starting with the release of Magento Commerce 2.3.2, Magento will assign and publish indexed Common Vulnerabilities and Exposures (CVE) numbers with each security bug reported to us by external parties. This allows users of Magento Commerce to more easily identify unaddressed vulnerabilities in their deployment. You can learn more about CVE identifiers at [CVE](https://cve.mitre.org/).

### Infrastructure improvements

This release contains enhancements to core quality, which improve the quality of the Framework and these functional areas: Customer Account, Catalog, CMS, OMS, Import/Export, Promotions and Targeting, Cart and Checkout, and Staging and Preview.

### Platform enhancements

*  [**Elasticsearch 7.9.x is now supported**]({{ page.baseurl }}/install-gde/system-requirements.html#elasticsearch). Although we recommend running Elasticsearch 7.9.x, Magento 2.4.x remains compatible with Elasticsearch 7.4.x. <!--- MC-36867-->

*  Magento 2.4.2 has been tested with [Varnish 6.4]({{ page.baseurl }}/install-gde/system-requirements.html#technologies-magento-can-use). Magento 2.4.x remains compatible with Varnish 6.x.

*  [**Redis 6.x is now supported**]({{ page.baseurl }}/install-gde/system-requirements.html#technologies-magento-can-use). Magento 2.4.x remains compatible with Redis 5.x. <!--- MC-34853-->

*  Magento 2.4.2 is now compatible with **Composer 2.x**. We recommend that merchants migrate to Composer 2.x. Although you can install this release using Composer 1.x, Composer 1.x will soon reach end-of-life. For an overview of Composer 2.x features, see [Composer 2.0 is now available!](https://blog.packagist.com/composer-2-0-is-now-available/)

The ability to configure a Magento installation to use a split database has been deprecated in this release. Merchants who currently use split database should start planning to revert to or migrate to a single database or use an alternative approach. See the [Deprecation of split database functionality in Magento Commerce](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) DevBlog post for an overview of this issue.  See [Revert from a split database to a single database]({{ page.baseurl }}/config-guide/revert-split-database.html) for migration instructions.

### Performance enhancements

This release includes code enhancements that boost API performance and Admin response time for deployments with large catalogs. Multiple scalability enhancements enable Magento 2.4.2 to natively support complex catalogs up to 20x larger than in previous releases.

### Adobe Stock Integration

This release includes Adobe Stock Integration v2.1.1.

### GraphQL

This release adds GraphQL coverage for the following features:

*  GraphQL now honors catalog permissions. Magento restricts which items are returned for a `products` query, based on the shopper's customer group <!--- MC-37388-->

*  Added the [`generateCustomerTokenAsAdmin`]({{ page.baseurl }}/graphql/mutations/generate-customer-token-as-admin.html) mutation and updated the `Customer` object to support remote purchasing assistance.

*  Added localization support across stores to support tasks such as changing languages, carts, and currencies. <!--- MC-37801-->

*  The GraphQL schema has been enhanced to optimize product data retrieval for configurable products with many variants. <!--- MC-36138-->

*  Integer type object IDs have been deprecated in favor of `uid` attributes of type ID. <!--- MC-36346-->

*  Added the `staging` attribute to the [`ProductInterface`]({{ page.baseurl }}/graphql/interfaces/product-interface.html) and [`CategoryInterface`]({{ page.baseurl }}/graphql/interfaces/category-interface.html) to determine if a product is staged and to view its associated campaign information. <!--- MC-33897-->

See the [GraphQL Developer Guide]({{page.baseurl}}/graphql/) for details on these enhancements.

### PWA Studio

This release of PWA Studio includes:

*  Internationalization and localization. Venia now provides support for multiple languages and currencies.

*  Support for multiple stores.

*  Enhanced extensibility.

*  Performance optimizations. Client-side performance has been enhanced with Google Lighthouse.

*  Introduction of My Account for Venia. This introduction of My Account features including order history (details), address book, and saved payments.

For information about enhancements and bug fixes, see [PWA Studio releases](https://github.com/magento/pwa-studio/releases). See [Magento compatibility](https://magento.github.io/pwa-studio/technologies/magento-compatibility/) for a list of PWA Studio versions and their compatible Magento core versions.

### Media Gallery

**New Role Resources for Media Gallery**. This release provides merchants the ability to limit administrator access to only the Media gallery and to control who can perform these actions:

*  Insert media assets into content

*  Upload assets

*  Edit assets details

*  Delete assets from the Media Gallery

*  Manage folder structure.

**Web-optimized images in content**. Merchants can now use [web-optimized image rendition](https://docs-beta.magento.com/user-guide/cms/media-gallery-image-optimization.html) in content instead of high resolution images. The original image remains unmodified in the Media Gallery, and the image rendition is dynamically generated when the image is inserted in the content.

### Magento Functional Testing Framework (MFTF)

MFTF 3.2.1 is now available. This release introduces error tolerance in both tests and test suit generation. Additional enhancements and bug fixes are described in the [Magento Functional Testing Framework Changelog](https://github.com/magento/magento2-functional-testing-framework/blob/develop/CHANGELOG.md).

### Vendor Developed Extensions

See the following articles for updates on features and changes for this release:

*  [Amazon Pay](https://docs.magento.com/user-guide/payment/amazon-pay.html)

*  [Braintree](https://docs.magento.com/user-guide/payment/braintree.html)

*  [dotdigital Engagement Cloud](https://docs.magento.com/user-guide/marketing/dotdigital/engagement-cloud.html)

*  [Klarna](https://docs.magento.com/user-guide/payment/klarna.html)

*  [Vertex Cloud](https://docs.magento.com/user-guide/tax/vertex.html)

*  [Yotpo Product Reviews]({{ site.baseurl }}/extensions/vendor/yotpo/release-notes.html)

### AWS S3 support enhancements

Amazon Simple Storage Service (AWS S3) support has been enhanced to include support for:

*  Object storage and future extensibility

*  [Storing media files]({{ page.baseurl }}/config-guide/remote-storage/config-remote-storage.html) on AWS S3

Support for AWS S3 has been added to all modules including B2B, PageBuilder, and Adobe Stock Integration.

## Fixed issues

We have fixed hundreds of issues in the Magento 2.4.2 core code.

### Installation, upgrade, deployment

<!--- MC-38429-->

*  The ability to configure a Magento installation to use a split database has been deprecated in this release. See the DevBlog post for a discussion of how to revert to a single database deployment.

<!--- MC-36472-->

*  Merchants can now successfully upgrade an Open Source deployment that runs MySQL 8.x to  a Commerce deployment. Previously, Magento threw an exception when AUTO_INCREMENT values reverted to initial values for all tables where `row_id` was added during upgrade.

<!-- ENGCOM-7280 -->

*  Magento now displays an error message that identifies the path that was used to create the patch if an error occurs when running `setup:db:generate-patch`. [GitHub-27523](https://github.com/magento/magento2/issues/27523)

<!-- ENGCOM-8029 -->

*  `block_html`, `full_page`, and `layout` caches are now disabled as expected after `setup:upgrade` execution.  [GitHub-28186](https://github.com/magento/magento2/issues/28186)

<!-- ENGCOM-8184 -->

*  The minimum required PHP version in `bootstrap.php` has been updated. [GitHub-30004](https://github.com/magento/magento2/issues/30004)

<!--- MC-38788-->

*  You can now execute `setup:upgrade` after installing sample data. Previously, when you tried to execute `setup:upgrade`, Magento displayed this error: `unable to apply data patch magento\catalogrulesampledata\setup\patch\data\installcatalogrulesampledata for module magento_catalogrulesampledata`. Magento also displayed this error in the system log: `main.ERROR: Sample Data error: Unable to unserialize value. Error: Syntax error`. [GitHub-30685](https://github.com/magento/magento2/issues/30685)

<!--- MC-36785-->

*  You can now set a YouTube API key from the command line as expected. Previously, Magento returned this error when you tried to execute `bin/magento config:sensitive:set catalog/product_video/youtube_api_key`: `There are no sensitive configurations to fill`.

<!-- ENGCOM-8163 -->

*  Magento now honors the `maxMessages` values that are defined in `queue_consumer.xml`. Previously, Magento used only the deployment configuration values. [GitHub-29522](https://github.com/magento/magento2/issues/29522)

### Adobe Stock Integration

<!--- ENGCOM-8020-->

*  Added support for reading `exif_image.png` or `exif-image.jpeg` metadata. [GitHub-1449](https://github.com/magento/adobe-stock-integration/issues/1449)

### Analytics

<!--- MC-37137-->

*  Advanced Reporting now works as expected for multiple environments in same domain. Previously, CSV files that were generated by Advanced Reporting failed because double quotes were escaped with backslashes rather than with another double quote as required by CSV standard RFC4180.

<!--- MC-35996-->

*  The `analytics_collect_data` job now runs successfully when using either the default or non-default port to connect to MySQL in `env.php`. Previously, `analytics_collect_data` threw an error when you used the non-default port.

<!--- MC-35407-->

*  CSV files that are generated by `analytics_collect_data` are now properly escaped. Previously, these files were not generated with the correct escaping, which prevented the generation of Inventory reports.

### Braintree

*  Shoppers can now use Apple Pay to successfully place an order for virtual products. Previously, Magento threw this error:  `There are no shipping methods available for you right now. Please try again or use an alternative payment method`.

*  The default PayPal Express Checkout payment method now works as expected with the Braintree Credit Card payment method. Previously, Magento did not display the **PayPal** button when the Braintree Credit Card payment method was enabled.

### Bundle products

<!--- MC-34063-->

*  Magento no longer sets prices for fixed-price bundle product child items in quotes.

<!--- MC-38050-->

*  Price sorting now works as expected when bundle products include out-of-stock products. Previously, sorting price in descending order did not display products in order of decreasing price.

<!--- MC-38576-->

*  Magento now automatically applies a default quantity of 1 for bundle product options when many options exist. Previously, merchants had to manually assign a default quantity to each option.

<!-- ENGCOM-8159 -->

*  The order invoice create page now displays the child products for bundle products as expected. [GitHub-27350](https://github.com/magento/magento2/issues/27350)

<!--- MC-38460 -->

*  Magento now assigns correct product prices when you re-order simple products that are part of a bundle product with a custom price. Previously, setting a custom price on a bundle product resulted in incorrect prices on attached simple products when reordered. [GitHub-30343](https://github.com/magento/magento2/issues/30343)

<!--- MC-30348 -->

*  Calling POST `/V1/order/{orderId}/ship` to ship an order that contains a bundle product now marks the order as complete as expected. Previously, Magento displayed this error message: `You can't create a shipment without products`. [GitHub-9762](https://github.com/magento/magento2/issues/9762)

### Cart and checkout

<!--- MC-34264-->

*  The shipping method estimator now works as expected when custom address attributes are present on the shipping step of the checkout workflow. Previously, Magento displayed this error message: `{"message":"Error occurred during \"custom_attributes\" processing. A custom attribute is specified with a missing attribute code. Verify the code and try again."}` [GitHub-27505](https://github.com/magento/magento2/issues/27505)

<!--- MC-35783-->

*  Magento now displays the `You have no items in your shopping cart` message in the mini cart as expected when a shopper removes the only item in their cart. Previously, cart data was not updated for 'checkout/cart/removeFailed' when a shopper removed the single item, and Magento displayed this message: `1 product requires your attention`.

<!--- MC-36088-->

*  Magento no longer displays the cost of shipping for an order for a non-applicable shipping method. Previously, Magento displayed a price of 0 for a non-applicable shipping method in the checkout workflow.

<!--- MC-36598-->

*  A customer’s default billing address is now selected when the **My billing and shipping address are the same** checkbox on the checkout workflow is unselected.

<!--- MC-37351-->

*  Cart contents are no longer lost when a shopper switches from one store to another in a different domain.

<!--- MC-38000-->

*  Shoppers can now successfully complete an order using Check Out with Multiple Addresses when using multiple shipping methods. Previously, Magento displayed this error: `There has been an error processing your request`. [GitHub-30197](https://github.com/magento/magento2/issues/30197)

<!--- MC-38048-->

*  Magento now displays the correct default country on the shipping page of the checkout workflow when the shopper changes the store view from the shopping cart.

<!--- MC-38309-->

*  Magento now excludes the current session when cleaning up customer sessions after a post-logout password reset when a guest shopper is logged in. Previously, Magento emptied the shopping cart when the shopper reset their password.

<!--- MC-36884-->

*  Magento now displays the correct default country for a store view when a shopper changes the store view in the shopping cart. Previously, when the store view was changed in the cart, the default country was incorrect.

<!--- MC-38746-->

*  Redundant calls to the `/rest/V1/guest-carts/cart_id/totals-information` endpoint on the cart have been removed, which has improved cart performance. Previously, when a shopper added a product to the cart and then subsequently viewed the cart, Magento called the `collectAddressTotals` method multiple times.

<!--- MC-38833-->

*  Magento no longer displays the **Region** field for a country in the checkout workflow when the **Allow to Choose State if It is Optional for Country** setting is disabled. [GitHub-30747](https://github.com/magento/magento2/issues/30747)

<!--- MC-38813-->

*  Magento no longer repeats a shipping address in the storefront checkout workflow when an order is re-ordered from the Admin.

<!--- MC-38814-->

*  Corrected problems with the design of `AdminMediaGalleryInsertLargeImageFileSizeTest`.

<!--- MC-37321-->

*  All new records in the `quote` table for guests are now assigned a value of 1 in the `customer_is_guest field`. Previously, for each new guest who added a product into cart, the record was assigned a 0 in the`quote.customer_is_guest` field.

<!-- ENGCOM-8091 -->

*  The **Submit** button on the Review & Payments  section of the checkout workflow has been moved to inside `<form id="purchaseorder-form"...></form>`, which makes implicit form submission possible without altering any JavaScript. [GitHub-27925](https://github.com/magento/magento2/issues/27925)

<!-- ENGCOM-8428 -->

*  Magento no longer displays the **Region** field on the checkout workflow when the **Allow to Choose State if It is Optional for Country** setting is disabled. [GitHub-30747](https://github.com/magento/magento2/issues/30747)

<!-- ENGCOM-8442 -->

*  Magento now correctly updates a cart’s item subtotal when a shopper clicks **Update Shopping Cart** when checking out with multiple addresses. [GitHub-30408](https://github.com/magento/magento2/issues/30408)

<!-- ENGCOM-8283 -->

*  Magento no longer throws an exception when `config.xml` nodes exist for payment methods that are not currently installed. Previously, Magento threw an exception during checkout. [GitHub-29555](https://github.com/magento/magento2/issues/29555)

<!-- ENGCOM-8215 -->

*  Magento now renders product names that contain special character correctly in the mini cart.[GitHub-29075](https://github.com/magento/magento2/issues/29075)

### Cart price rule

*  Cart price rules are now applied as expected when order subtotals are calculated without incorporating tax. The new `Subtotal (Incl. Tax)` option has been added as a cart price rule condition.

<!--- MC-37884-->

*  Applying a price rule with a coupon using GraphQL now works as expected when the **Fixed amount discount for whole cart** action is used.

### Catalog

<!--- MC-34100-->

*  Magento now displays all re-enabled products in the storefront as expected. Previously, when a product was disabled and then re-enabled, Magento did not display the product until the Varnish page cache was cleared or the store re-indexed because the page cache was not invalidated after re-enabling a product.

<!--- MC-37745-->

*  Partial re-indexing of large catalogs now works as expected. Previously, products randomly disappeared from the storefront category page  during re-indexing with the `catalogsearch_fulltext` partial indexer.

<!--- MC-35123-->

*  Shoppers can now re-order an invoiced order of a product with customizable options as expected. Previously, Magento threw this error when a shopper tried to re-order: `{"0":"The product's required option(s) weren't entered. Make sure the options are entered and try again`.

<!--- MC-35212-->

*  You can now successfully set the **Layout** setting on the Category Design page to **No layout updates**. Previously, Magento reverted to **Category - FullWidth** when you assigned the **No layout updates** value.

<!--- MC-35490-->

*  Problems with product sort order on the storefront have been resolved. Previously, when Magento indexed product prices, it occasionally set a configurable product’s `min_price` and `max_price` to 0 in the `catalog_product_index_price` table, which affected price sort order on the storefront.

<!--- MC-35608-->

*  Magento now successfully updates attributes that are labeled `Product Type`. Previously, because the `product_type` attribute is reserved in the Magento core code, Magento displayed this message when you tried to update a `Product Type` attribute: `An attribute with the same code (product_type) already exists.`

<!--- MC-36214-->

*  Magento no longer changes the position of an uploaded video in the Images and Videos section of the product details page when you save the product. Previously, the new image position was assigned an index value (position in the list) and if existing image positions were not aligned with their indices values, the new image was misplaced in the list.

<!--- MC-36548-->

*  The **Add to Cart** functionality now works as expected whenever the **Add to Cart** button ia available to click. Previously, if you clicked this button multiple times while waiting for a product page to load, Magento threw this error: `Invalid Form Key. Please refresh the page`.

<!--- MC-36835-->

*  Magento no longer flushes category cache when you add or save a disabled product to a category. Previously, Magento flushed the cache for related categories despite the product status, which affected server performance.

<!--- MC-37006-->

*  Magento no longer flushes category cache when a merchant adds or removes disabled products to or from a category. Previously, Magento flushed the cache for related categories despite product status. Categories were also unassigned when a category was saved, which led to flushing of category cache.

<!--- MC-37347-->

*  Catalog product filtering within the **All store view** scope now works correctly. Previously, products with a status of either `Enabled` or `Disabled` were displayed in the grid while filtering only enabled or disabled products.

<!--- MC-38038-->

*  Partial re-indexing no longer results in missed products and empty categories.

<!--- MC-38315-->

*  Re-order now works as expected when **Use JavaScript Calendar** is enabled (**Stores** > **Configuration** > **Catalog** > **Date & Time Custom Options**). Previously, when this setting was enabled, Magento displayed this error when you tried to re-order the previously placed order from the Admin: `Please specify date required option(s)`.

<!--- MC-38719-->

*  Magento now displays the correct currency in multi-site deployments during tier price creation.

<!--- MC-38914-->

*  Product image custom attributes are now correctly escaped. The `data-src` attribute has the same value as `src` attribute, as expected. Previously, URL special symbols were escaped.

<!--- MC-37665-->

*  Updating a category through the REST API no longer disables the **Use Default Value** setting on the Enable Category, Include in Menu, and URL Key attributes.

<!--- MC-35363-->

*  Saving a category now flushes only the block cache that is related to this category. Previously, Magento flushed the cache for all category blocks.

<!--- MC-30626-->

*  The price of a custom option with a percent price is now converted as expected into the active store’s base currency in multi-store deployments. Previously, the price of a custom option with a percent price was converted incorrectly. [GitHub-26432](https://github.com/magento/magento2/issues/26432)

<!--- MC-38890-->

*  Magento now recreates images successfully, and these images are visible in the Admin as expected whenever a merchant sends media gallery data using POST `rest/all/V1/products`. Previously, Magento recreated the images but deleted them when a merchant sent media gallery data via POST `rest/all/V1/products` if the images were deleted in `pub/media` but there were still records in media still contained records for these images. As a result, the merchant saw only placeholders in the Admin because the images were created and deleted during the update process.

<!--- MC-36903-->

*  Records are now deleted as expected when you unassigned an item from a website. Previously, images were duplicated when POST `rest/all/V1/products` was executed.

<!--- MC-38413-->

*  The `/V1/categories/{categoryId}/products` call now returns a list of all products that belong to the parent category as expected. Previously, if a product belonged to more than one subcategory of the parent category, Magento threw this type of error: `Internal Error. Details are available in Magento log file. Report ID: webapi-5f8579e37db54`.  [GitHub-30461](https://github.com/magento/magento2/issues/30461)

<!--- MC-32996-->

*  The `/V1/products/attributes/:attributeCode/options` REST endpoint now supports updating an existing attribute option.

<!--- MC-30626 ENGCOM-8475-->

*  The price of a custom option with a percent price is now converted as expected into the active store’s base currency in multi-store deployments. Previously, the price of a custom option with a percent price was converted incorrectly. [GitHub-26432](https://github.com/magento/magento2/issues/26432)

<!-- ENGCOM-8395 -->

*  Merchants can now successfully save a new attribute during product creation. Previously, Magento did not save the attribute and redirected the merchant to the store view home page when they tried to save the attribute. [GitHub-30362](https://github.com/magento/magento2/issues/30362)

### Catalog Rule

<!--- MC-35065-->

*  Catalog price rules now work as expected with custom options on product detail pages. Previously, product prices on that page did not reflect applicable catalog price rules. [GitHub-22856](https://github.com/magento/magento2/issues/22856)

<!--- MC-34265-->

*  Product and catalog caches now expire as scheduled. Previously, caches expired daily because `сron` ran the `catalogrule_apply_all` task once daily, which re-indexed all catalog rules and dependent indexers, and cleared the cache for all products and categories.

### Cleanup

<!--- MC-37922-->

*  An extraneous HTML `<br>` tag has been removed from the Check Data message area of the  **System**  >  **Import** page.

<!-- ENGCOM-8101 -->

*  Removed unnecessary spaces in `app/code/Magento/Contact/view/frontend/templates/form.phtml`. [GitHub-29779](https://github.com/magento/magento2/issues/29779)

<!-- ENGCOM-7967 -->

*  The title of the Order Failure page has been revised for accuracy. Previously, this page was titled, **We received your order!** [GitHub-29416](https://github.com/magento/magento2/issues/29416)

<!-- ENGCOM-8028 -->

*  `ChangeQuoteControl` has been refactored. [GitHub-29673](https://github.com/magento/magento2/issues/29673)

<!-- ENGCOM-8027 -->

*  AccessChangeQuoteControl and its unit tests have been refactored. [GitHub-29672](https://github.com/magento/magento2/issues/29672)

<!-- ENGCOM-8053 -->

*  Corrected the code style of the return type declaration in `app/code/Magento/Captcha/CustomerData/Captcha.php`. [GitHub-29712](https://github.com/magento/magento2/issues/29712)

<!-- ENGCOM-7716 -->

*  Corrected typo in `setup:config:set`. [GitHub-28802](https://github.com/magento/magento2/issues/28802)

<!-- ENGCOM-8058 -->

*  Corrected grammar in the PHPDoc for the `framework/Registry.php` file. [GitHub-29661](https://github.com/magento/magento2/issues/29661)

<!-- ENGCOM-8288 -->

*  Corrected position of the button list on the New Attribute page.

<!-- ENGCOM-8315 -->

*  Added correct block class for the frontend `viewModel` reference example for the `\Magento\Framework\View\Element\Template` class. [GitHub-30450](https://github.com/magento/magento2/issues/30450)

<!-- ENGCOM-8090 -->

*  A redundant fieldset in the Sale Rule form has been removed. [GitHub-29599](https://github.com/magento/magento2/issues/29599)

<!-- ENGCOM-8273 -->

*  Removed extraneous whitespace from `app/code/Magento/Catalog/Helper/Product/View.php`. [GitHub-30601](https://github.com/magento/magento2/issues/30601)

<!-- ENGCOM-8448 -->

*  Unnecessary code has been removed from the hierarchy/edit.phtml template.

<!-- ENGCOM-8446 -->

*  Corrected PHPdoc comment in `app/code/Magento/CatalogImportExport/Model/Export/Product.php`. [GitHub-30833](https://github.com/magento/magento2/issues/30833)

<!-- ENGCOM-8181 -->

*  Corrected typo in function name in `app/code/Magento/Ui/view/base/web/js/form/element/ui-select.js`. [GitHub-29987](https://github.com/magento/magento2/issues/29987)

<!-- ENGCOM-8478 -->

*  Corrected the pluralization of “item” in the minicart and checkout order summary. [GitHub-29920](https://github.com/magento/magento2/issues/29920)

<!-- ENGCOM-8309 -->

*  Removed whitespace in inline elements in markup layered navigation filters. [GitHub-30448](https://github.com/magento/magento2/issues/30448)

<!-- ENGCOM-8277 -->

*  The docblock annotation for the PublisherInterface message has been corrected. [GitHub-30190](https://github.com/magento/magento2/issues/30190)

<!-- ENGCOM-8264 -->

*  Corrected arguments in the `getStatusByState` method. [GitHub-30173](https://github.com/magento/magento2/issues/30173)

<!-- ENGCOM-8235 -->

*  Corrected method description in `app/code/Magento/Quote/Model/Cart/Totals/ItemConverter.php`. [GitHub-30125](https://github.com/magento/magento2/issues/30125)

<!-- ENGCOM-8242 -->

*  Removed redundant variable assignments in the same line in multiple files. [GitHub-30133](https://github.com/magento/magento2/issues/30133)

<!-- ENGCOM-8263 -->

*  Changed `@param string $attribute` to  `@param AbstractAttribute|string[]|string $attribute` in `EntityAbstract.php`. [GitHub-30191](https://github.com/magento/magento2/issues/30191)

### Configurable products

<!--- MC-35016-->

*  Filtering out-of-stock configurable products by price now displays results within the correct price range.

<!--- MC-38930-->

*  A virtual product no longer changes type when its status is changed from enabled to disabled (or vice versa). Previously, Magento changed a product’s type from virtual to simple when its status changed.

<!--- MC-38197-->

*  The `getValue()` method no longer triggers a fatal error when updating carts.

<!--- MC-34444-->

*  Configurable products that are available on multiple websites no longer show simple child products that are not assigned to the specific website. [GitHub-28291](https://github.com/magento/magento2/issues/28291)

<!-- ENGCOM-8202 -->

*  Storefront product pages now display tier prices without taxes as expected. [GitHub-12225](https://github.com/magento/magento2/issues/12225)

### cron

<!--- MC-37712-->

*  The System Message list now accurately reflects product updates after `cron` has run and Magento has updated products as scheduled.

### Custom customer attributes

<!--- MC-23545-->

*  Magento now displays customer attributes of type `file` on the Account Information page after creation. Previously, when you tried to save a new attribute of this type, Magento displayed these errors: `The "newAttribute" attribute value is empty. Set the attribute and try again` and `’Validation is failed`.

<!--- MC-23544-->

*  Magento now correctly displays multi-line custom customer attribute values. Previously, not all data was displayed.

<!--- MC-36978-->

*  Magento now alerts shoppers when they enter an invalid birth date while creating an account. Previously, the validator disregarded locale settings, and shoppers were redirected to the Create New Customer Account Page with an invalid date error.

<!--- MC-38846-->

*  Custom address attributes are now included as expected in the Payment step of checkout workflow.

<!--- MC-38114-->

*  Custom address multi-select attributes are now correctly displayed during guest checkout and on the Admin and My Account order details page.

<!--- MC-37101-->

*  You can now delete a leading zero in a custom customer attribute when `Input Type` is set to `Text` and `Input Validation` is set to `Numeric Only`.

<!--- MC-36721-->

*  Magento now successfully exports customer data that includes a custom gender attribute value.

### Customer

<!--- MC-35771-->

*  The calendar widget for the storefront customer account page date of birth field now uses the designated store locale.

<!--- MC-38498-->

*  Magento no longer saves duplicate entries of a customer address during checkout of a re-order for an existing customer from the Admin.

<!--- MC-37393-->

*  Deleting all addresses from multiple customers from the Admin now deletes all addresses from the customer address list and removes default billing and shipping addresses. Previously, Magento deleted the address from the customer address list but did not remove the default billing and shipping addresses.

<!--- MC-37377-->

*  The Admin customer address tab now correctly displays address count after an administrator has performed a mass deletion of addresses. Previously, Magento included deleted addresses in its count.

<!--- MC-36718-->

*  The DateTime format for the **Date of Birth** field on the customer registration page has been corrected. Previously, the leading zero that preceded a single-digit day was missing.

<!--- MC-36024-->

*  Date format validation for the **Date of Birth** field now works before the shopper clicks the **Create an account** button. Previously, a shopper could enter a value in an invalid format, and when they clicked the **Create an account** button, the shopper was redirected to the Create New Customer Account Page with an invalid date error.

<!--- MC-33867-->

*  Magento no longer throws a fatal error when an administrator tries to save a new customer account that contains invalid data for an attribute.

<!--- MC-36258-->

*  Magento no longer throws a 400 error when a customer tries to access their shopping cart in a deployment where Magento Shipping was previously installed and the default Luma theme is currently deployed. Previously, Magento did not filter out section names that were created by previously installed/enabled modules that were not supported in the Admin before sending requests to the server, which generated errors.

<!--- MC-35812-->

*  Magento now displays a message as expected when a shopper creates a guest account when the **Require Emails Confirmation setting is enabled** and `Magento\Customer\Controller\Account\CreatePost` has been overridden. Previously, Magento did not permit this type of customization of the user registration process, and under these conditions, a user's email confirmation status was considered complete, the new user was automatically logged in, and no error message was shown.

### dotdigital

*  Error handling has been improved when retrieving lists of programs from dotdigital Engagement Cloud.

*  The value that is synced in the store name column during guest sync is now the store view name as expected. Previously, the website name was included in this column.

*  Added an array check before looping over order status automations after an order is saved.

*  Resolved issues with Composer upgrades that were the result of the dotdigital module’s dependency on `magento/module-authorization`.

### Downloadable

<!-- ENGCOM-7679 -->

*  Magento no longer lists a downloadable product in My Download Products tab after the order that it belongs to has been partially refunded. [GitHub-28388](https://github.com/magento/magento2/issues/28388

### EAV

<!--- MC-35934-->

*  Custom attributes that use `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` now use default values if no value is provided in the payload when a product is created by API call.

### Email

<!-- ENGCOM-7961 -->

*  `\Magento\Config\Model\Config\Source\Email\Template::toOptionArray` no longer throws an error when `setPath()` is not called before `toOptionArray()`. [GitHub-29315](https://github.com/magento/magento2/issues/29315)

<!--- MC-36777-->

*  Magento now correctly converts plain text to HTML when you click **Return Html Version** when loading an email template.

<!--- MC-34803-->

*  Email sent to customers that contain partial invoices now includes accurate item subtotals. Previously, the subtotal in this email was the total of the ordered quantity, not the total amount of the invoiced quantity.

<!--- MC-38337-->

*  Magento now sends email reminders to all relevant customers with valid email addresses. Previously, Magento stopped sending reminder emails to customers after encountering one invalid address.

### Frameworks

<!--- MC-24195-->

*  Customized filter groups are now applied correctly when searching on customers. Previously, the `afterSearch` function did not OR filters as expected. [GitHub-24576](https://github.com/magento/magento2/issues/24576)

<!--- MC-36942-->

*  Images on a store’s home page are now rendered successfully. Previously, the page source HTML was corrupted because the three consecutive slashes in the image’s base64 code was misinterpreted as a comment.

<!--- MC-37369-->

*  DatePicker now works correctly when filtering orders on the Admin Orders list in stores using the Arabic locale (`ar_SA - Saudi Arabia`).

<!--- MC-38344-->

*  DatePicker now displays the correct date after a merchant saves a cart price rule in a deployment that implements a Dutch (Netherlands) locale. [GitHub-30382](https://github.com/magento/magento2/issues/30382)

<!--- MC-31085-->

*  Magento now correctly represents Arabic thousands grouping and Arabic decimal separator symbols. Previously, Arabic symbols were trimmed. [GitHub-26676](https://github.com/magento/magento2/issues/26676)

<!--- MC-30631-->

*  Magento now deletes expired database sessions from the database `session` table as expected.

### General fixes

<!--- MC-38105-->

*  You can now configure a native session handler that differs from the handler that is defined in `php.ini`. Previously, `SessionManager` did not set the memcache as `save_handler`, but instead used the file’s `session_handler`. Magento threw this error: `main.CRITICAL: Warning: SessionHandler::read(): open(127.0.0.1:11211/sess_0imeeaqmnvemdg4e3h57tat0ik, O_RDWR) failed: No such file or directory (2) in../vendor/magento/framework/Session/SaveHandler/Native.php on line 22 {"exception":"[object] (Exception(code: 0): Warning: SessionHandler::read(): open(127.0.0.1:11211/sess_0imeeaqmnvemdg4e3h57tat0ik, O_RDWR) failed: No such file or directory (2) in ../vendor/magento/framework/Session/SaveHandler/Native.php on line 22 at ../vendor/magento/framework/App/ErrorHandler.php:61)”}`. [GitHub-24717](https://github.com/magento/magento2/issues/24717)

<!-- ENGCOM-8052 -->

*  The following improvements have been made to the `LoginAsCustomer` modules:

   *  Replaced the `around` plugin with `after`

   *  Removed redundant code

   *  Replaced `(bool)->getValue()` with `isSetFlag`. [GitHub-29689](https://github.com/magento/magento2/issues/29689)

<!-- ENGCOM-8117 -->

*  Unused parameters in the construct of the `AdvancedPricing` class have been removed. [GitHub-29531](https://github.com/magento/magento2/issues/29531)

<!-- ENGCOM-8018 -->

*  Magento now downloads inline translations JavaScript modules only when they are enabled.  [GitHub-29553](https://github.com/magento/magento2/issues/29553)

<!-- ENGCOM-8093 -->

*  Reloading all customer-data sections by wildcard (*) no longer causes requests to `customer/section/load` to throw a 400 error. [GitHub-28154](https://github.com/magento/magento2/issues/28154)

<!-- ENGCOM-7994 -->

*  Magento now passes exceptions that occur when a layout is rendered in production mode to `var/report`. [GitHub-29606](https://github.com/magento/magento2/issues/29606)

<!--- MC-35058-->

*  Merchants can now unassign products from categories as expected. Previously, Magento threw an error similar to this error: `Could not save product "4" with position 0 to category 3`.

<!-- ENGCOM-7527 -->

*  Magento now throws an exception when a customer who does not exist requests a password reset. [GitHub-26288](https://github.com/magento/magento2/issues/26288)

<!--- MC-33687 ENGCOM-8497-->

*  Magento now displays an informative error message when an administrator tries to save a customer account that contains an invalid value for a customer attribute  while uploading a file that this attribute value. Previously, Magento threw a fatal error. [GitHub-30295](https://github.com/magento/magento2/issues/30295)

<!-- ENGCOM-8400 -->

*  Magento now applies the **Logo for HTML Print View** configuration setting to storefront invoice PDFs as expected. [GitHub-24730](https://github.com/magento/magento2/issues/24730)

<!-- ENGCOM-8425 -->

*  `static::` has been replaced with `self::` throughout the codebase for accessing private constants. [GitHub-30781](https://github.com/magento/magento2/issues/30781)

<!-- ENGCOM-8395 -->

*  Magento now opens the New Attribute page as expected when a merchant clicks the **Create New Attribute** button twice during product creation.  Previously, Magento displayed an empty page and threw an error. [GitHub-30361](https://github.com/magento/magento2/issues/30361)

<!-- ENGCOM-8426 -->

*  Magento no longer displays the `The coupon code has been accepted` message after a coupon has been removed. [GitHub-30255](https://github.com/magento/magento2/issues/30255)

<!-- ENGCOM-8396 -->

*  Administrators can now assign widgets to specific categories. [GitHub-30009](https://github.com/magento/magento2/issues/30009)

<!-- ENGCOM-8216 -->

*  Attribute selector `input[type=datetime]` has been replaced with a less specific input type selector. [GitHub-30064](https://github.com/magento/magento2/issues/30064)

<!-- ENGCOM-8282 -->

*  Magento now displays store-specific values that are associated with custom category  attributes as expected. [GitHub-13440](https://github.com/magento/magento2/issues/13440)

<!-- ENGCOM-8287 -->

*  Magento now displays a prompt asking whether the customer group should be changed when you click the **Validate VAT Number** button on the order creation page when the store address and shipping destination belong to different EU countries. [GitHub-29652](https://github.com/magento/magento2/issues/29652)

<!-- ENGCOM-8031 -->

*  The `\Magento\Catalog\Model\ImageUploader` class has been refactored to use the new `moveFileFromTmp`  method. [GitHub-29598](https://github.com/magento/magento2/issues/29598)

<!-- ENGCOM-8178 -->

*  Magento now displays a more informative error message when a merchant tries to create a product attribute with `product_type` and `type_id` codes to be more descriptive. [GitHub-28479](https://github.com/magento/magento2/issues/28479)

<!-- ENGCOM-8135 -->

*  Corrected validation logic for the **Customer Token Lifetime (hours)**  and **Admin Token Lifetime (hours)** fields  on the Admin **Stores**  >  **Configurations** >  **Services**  > **OAuth** page. [GitHub-29502](https://github.com/magento/magento2/issues/29502

<!-- ENGCOM-8132 -->

*  Magento now correctly parses text that contains }} in the widget content field. [GitHub-12087](https://github.com/magento/magento2/issues/12087)

<!-- ENGCOM-8098 -->

*  You can now remove a filter from the Product Categories page. Previously, when you tried to delete the filter, Magento did not let you remove the filter and displayed this error:  `Something went wrong`. [GitHub-8538](https://github.com/magento/magento2/issues/8538)

### GraphQL

<!--- MC-37615-->

*  The GraphQL URL resolver now handles query parameters correctly. Previously, it returned NULL when handling SEO-friendly URLs with parameters.

<!-- ENGCOM-8422 -->

*  The GraphQL URL resolver now handles CMS page hierarchy correctly. Previously, it returned NULL. [GitHub-30474](https://github.com/magento/magento2/issues/30474)

<!--- MC-38209-->

*  Queries for a product's `categories.breadcrumbs` data no longer return breadcrumb data for categories whose parent category is disabled. [GitHub-30468](https://github.com/magento/magento2/issues/30468)

<!--- MC-38407-->

*  The path to a category image is now returned correctly when URL rewrites are disabled.

<!--- MC-36648-->

*  Magento now returns a more informative message when an error occurs with during a GraphQL password reset operation. [GitHub-30179](https://github.com/magento/magento2/issues/30179)

<!--- MC-38078-->

*  Products positions are now updated as expected in GraphQL query results when the query results are cached.

<!--- MC-35355-->

*  The `products` query now returns the expected results when the `category_id`  filter is specified with the `in` keyword. [GitHub-30349](https://github.com/magento/magento2/issues/30349)

### Grouped products

<!--- MC-35361-->

*  The products query now returns all expected data for grouped products. Previously, `product_links` was an empty array.

<!--- MC-37718-->

*  A grouped product is now listed as out-of-stock on the product edit page when all child simple products are out-of-stock.

<!--- MC-37249-->

*  The status of a grouped product now updates correctly on the product edit page when the status of its child simple products changes to out-of-stock. Previously, the inventory stock item for the parent of the grouped product did not update after its children changed stock status.

### Images

<!--- MC-36942-->

*  Images on a store’s home page are now rendered successfully. Previously, the page source HTML was corrupted because the three consecutive slashes in the image’s base64 code was misinterpreted as a comment.

<!-- ENGCOM-8116 -->

*  The dependency on the `fileinfo` extension has been removed from the CMS module. Previously, Magento threw an error when you tried to upload an image using the image uploader, which is launched when you click the Insert Image button when adding content. [GitHub-24332](https://github.com/magento/magento2/issues/24332), [GitHub-16531](https://github.com/magento/magento2/issues/16531), [GitHub-29852](https://github.com/magento/magento2/issues/29852)

<!-- ENGCOM-8020 -->

*  Added support for reading `exif_image.png` or `exif-image.jpeg` metadata. [GitHub-1449](https://github.com/magento/adobe-stock-integration/issues/1449)

### Import/export

<!--- MC-35081-->

*  Customer address `region_id` is no longer assigned a `NULL` value when you import customer addresses using a CSV file (`entity type = "customer address"` and `import behavior = "add/update”`) from which certain field values have been deleted.

<!--- MC-35295-->

*  You can now hide product images on the storefront during import.

<!--- MC-35836-->

*  When an imported product has `qty` set to 0 but `is_in_stock set` to 1 in the CSV file, the product is not listed on the category page, and the product details page identifies it as out-of-stock. Previously, products with these values were visible on the storefront after import.

<!--- MC-38433-->

*  CSV import no longer ignores the `dropdown` and `textarea` values for additional attributes. Previously, these attribute values were not updated during import.

<!--- MC-37933-->

*  The product export CSV file now appears in the Admin list of export CSV files as expected. Previously, Magento threw an error when you ran this command: `bin/magento queue:consumers:start exportProcessor --single-thread --max-messages=10000`.

<!--- MC-37672-->

*  Magento no longer throws an error when importing CSV data that includes Bengali (Bangla) alphabet characters.

<!--- MC-36410-->

*  Magento now displays an informative error message when an administrator clicks **Check Data** during import of a file that has been changed since export when working in Chrome. Previously, Magento displayed a console error but did not tell the user how to proceed.

<!-- ENGCOM-8252 -->

*  Magento no longer duplicates product images when you import the same product CSV data more than once. [GitHub-21885](https://github.com/magento/magento2/issues/21885)

<!-- ENGCOM-8262 -->

*  The limit of 90 characters for image file names  in `vendor/magento/framework/File/Uploader.php` has been removed.  Previously, directory and file name length could not exceed 255 characters. Magento imported products with images whose file name exceeded this limit, but did not import the image file. [GitHub-29377](https://github.com/magento/magento2/issues/29377)

### Index

<!--- MC-38003-->

*  We have improved the performance of the partial indexer. Magento now clears the cache IDs that were changed for each 1000-ID batch iteration. Cache context no longer accumulate IDs. Previously, cache context accumulated cache IDs for each 1000-ID batch iteration and cleared the same set of IDs on each iteration.

<!--- MC-38168-->

*  We have resolved issues with the manual indexer that had resulted in either empty category pages or reduced product count on category pages. Issues with incomplete category pages or product count occurred when:

   *  the `catalogsearch_fulltext` and `catalog_product_price` partial indexers were executed on a large catalog until these indexers completed execution.

   *  the partial indexer was executed on either `catalog_category_product` or `catalog_product_category` indices, and at the same time a full re-index was executed on one of those indices. These two indexing processes could conflict, which resulted in products missing from category pages.

   *  `bin/magento indexer:reindex inventory` was executed on a large catalog, products were missing from category pages until the `catalogsearch_fulltext` partial indexer completed execution.

<!--- MC-39700-->

*  An indexer has been added to the `Magento_Bulk` MySQL table, which has improved the performance of bulk operations.

<!--- MC-38806-->

*  Comments in database tables now accurately reflect table status after re-indexing (`bin/magento indexer:reindex`). Previously, table comments after re-indexing contained the same values that comments contained after a fresh installation.

### Infrastructure

<!--- MC-34353-->

*  You can now use `app/etc/env.php` to change the message broker from MYSQL to AMQP.

<!--- MC-38242-->

*  Issues with the calculation of remainders for decimal values for product quantities have been corrected in the relevant JavaScript library. Magento previously calculated decimal fractions of more than two digits incorrectly and subsequently displayed an incorrect message.

<!--- MC-38993-->

*  The `\Magento\Authorization\Model\Rules::update` method has been deprecated.

<!-- ENGCOM-8000 -->

*  Magento no longer throws a fatal error when converting a date object from UTC. Previously, under certain conditions, the `convertConfigTimeToUtc` method threw an exception. [GitHub-29525](https://github.com/magento/magento2/issues/29525)

<!-- ENGCOM-7987 -->

*  `DataObject` has been replaced with the product model in `\Magento\MediaGalleryCatalogUi\Ui\Component\Listing\Columns\Thumbnail::prepareDataSource`.[GitHub-1711](https://github.com/magento/adobe-stock-integration/issues/1711)

<!-- ENGCOM-7914 -->

*  `RequireJS` resolver no longer fails to detect blocked resources. Previously, the resolver did not correctly detect whether all resources on a page were loaded or handled appropriately, and the page kept loading.  [GitHub-28116](https://github.com/magento/magento2/issues/28116)

<!-- ENGCOM-8229 -->

*  Attribute Repository code validation now respects `Magento\Eav\Model\Entity\Attribute::ATTRIBUTE_CODE_MAX_LENGTH` rather than a hard coded value. [GitHub-29017](https://github.com/magento/magento2/issues/29017)

<!--- MC-35699-->

*  HTML minification no longer strips triple slashes (///) from HTML strings in PHTML files. Previously, triple slashes were interpreted as comments during minification, and the rest of the line was completely removed in the generated PHTML file upon deployment.

<!--- MC-38201-->

*  Merchants can now configure indexer subscriptions on the table column level rather than the table level. A new argument has been added to `\Magento\Framework\Mview\View\Subscription` to allow  columns to be ignored for a specific view or table combination. [GitHub-30243](https://github.com/magento/magento2/issues/30243)

<!--- MC-30171-->

*  Clicking the **Add to Cart** button  before the product page JavaScript has fully initialized no longer results in duplicate `form_key` values. Previously, a product could be added to the cart with a cached `form_key` value that triggered an exception. When **Add to Cart** was clicked before the JavaScript had fully initialized, then the `form_key` value that was sent in the form data did not match the users session, and the product was not added to the cart. [GitHub-13746](https://github.com/magento/magento2/issues/13746)

<!-- ENGCOM-8107 -->

*  The current cURL client now respects case-insensitive header names. Previously, the `Set-Cookie` comparison was case-sensitive, which could cause problems with some HTTP servers. [GitHub-29524](https://github.com/magento/magento2/issues/29524)

<!-- ENGCOM-8360 -->

*  Updated XSD URN format in `api-functional` and test case XML files. [GitHub-30552](https://github.com/magento/magento2/issues/30552)

<!-- ENGCOM-8295 -->

*  An event prefix and event object has been added to the catalog product option value collection to improve customization of the collection loading of `\Magento\Catalog\Model\ResourceModel\Product\Option\Value\Collection`. [GitHub-29621](https://github.com/magento/magento2/issues/29621)

<!-- ENGCOM-8261 -->

*  All occurrences of `array_merge` have been refactored to use the format recommended in the Magento coding standard. [GitHub-30005](https://github.com/magento/magento2/issues/30005)

<!-- ENGCOM-7718 -->

*  A `head.additional` block of type `\Magento\Framework\View\Element\Text\ListText` has been added to the `adminhtml` `default` layout (by `magento2/module-base`). [GitHub-29165](https://github.com/magento/magento2/issues/29165)

<!-- ENGCOM-8312 -->

*  Added missing escape URL method to the layout template module widget. [GitHub-30036](https://github.com/magento/magento2/issues/30036)

<!-- ENGCOM-8127 -->

*  The `\Magento\Framework\Filesystem\Io\File::read()` method is now compatible with `\Magento\Framework\Filesystem\Io\IoInterface::read()`. [GitHub-27866](https://github.com/magento/magento2/issues/27866)

### Klarna

*  Removed the dependency on the PayPal module. [GitHub-29421](https://github.com/magento/magento2/issues/29421)

### Media Gallery

<!-- ENGCOM-8014 -->

*  The Admin **Stores**  >  **Configuration**  >  **Advanced**  >  **System** page has been updated to display the correct product name (Media Gallery). Minor redesigns to the user interface have been included. [GitHub-1738](https://github.com/magento/adobe-stock-integration/issues/1738)

<!-- ENGCOM-8019 -->

*  Links in the Used in section of Media Gallery image descriptions now display a grid that has been filtered by the selected image as expected. Previously, the displayed grid was not correctly titled, and list entries were not accurate. [GitHub-1694](https://github.com/magento/adobe-stock-integration/issues/1694)

<!-- ENGCOM-8019 -->

*  You can now successfully edit multiple images in the Media Gallery. Previously, you could not add tags to a second image after adding tags to one image. [GitHub-1755](https://github.com/magento/adobe-stock-integration/issues/1755)

<!-- ENGCOM-8015 -->

*  The Tags drop-down menu is now empty as expected after you remove tags from an image in the Media Gallery.  [GitHub-1703](https://github.com/magento/adobe-stock-integration/issues/1703)

### MFTF

<!-- ENGCOM-8359 -->

*  Replaced repetitive actions with action groups in `CheckStaticBlocksTest`. [GitHub-30561](https://github.com/magento/magento2/issues/30561)

<!-- ENGCOM-8267 -->

*  `AdminUpdateCategoryAndMakeInactiveTest` and `VerifyChildCategoriesShouldNotIncludeInMenuTest` have been refactored to comply with MFTF best practices. [GitHub-30058](https://github.com/magento/magento2/issues/30058)

<!-- ENGCOM-8458 -->

*  Removed duplicated `AdminOpenCMSBlocksGridActionGroup`. [GitHub-30896](https://github.com/magento/magento2/issues/30896)

<!-- ENGCOM-8156 -->

*  Replaced `AdminOpentCmsBlockActionGroup` with AdminOpenCmsBlockActionGroup. [GitHub-29839](https://github.com/magento/magento2/issues/29839)

<!-- ENGCOM-8226 -->

*  Deprecated `GoToAttributeGridPageActionGroup`. [GitHub-30103](https://github.com/magento/magento2/issues/30103)

<!-- ENGCOM-8061 -->

*  Added action groups to the `Analytics` module. [GitHub-29500](https://github.com/magento/magento2/issues/29500)

<!-- ENGCOM-7334 -->

*  Updated `CheckCheckoutSuccessPageAsRegisterCustomerTest` and `CheckCheckoutSuccessPageAsGuestTest` to cancel created orders after tests run. [GitHub-28324](https://github.com/magento/magento2/issues/28324)

<!-- ENGCOM-8214 -->

*  Removed `AdminNavigateToPageGridActionGroup` due to redundancy.[GitHub-29838](https://github.com/magento/magento2/issues/29838)

<!-- ENGCOM-7804 -->

*  Added test for enabling email to a friend in the Admin. [GitHub-29145](https://github.com/magento/magento2/issues/29145)

<!-- ENGCOM-8316 -->

*  Added test for deleting a CMS block from a grid by an administrator. [GitHub-30372](https://github.com/magento/magento2/issues/30372)

<!-- ENGCOM-8280 -->

*  An issue with `StorefrontProductListWidgetWithSharedCatalogTest` that caused the test to be skipped has been resolved. [GitHub-322](https://github.com/magento/partners-magento2b2b/issues/322)

<!-- ENGCOM-8268 -->

*  Corrected issues with skip in MFTF tests for CMS page for Media Gallery. [GitHub-30164](https://github.com/magento/magento2/issues/30164)

#### New action groups

*  `AssertStorefrontCustomerLogoutSuccessPageActionGroup`. [GitHub-29841](https://github.com/magento/magento2/issues/29841) <!-- ENGCOM-8121 -->

*  `AdminOpenConfigurationStoresPageActionGroup`. [GitHub-29848](https://github.com/magento/magento2/issues/29848) <!-- ENGCOM-8259 -->

*  `ReloadPageActionGroup`. [GitHub-30683](https://github.com/magento/magento2/issues/30683) <!-- ENGCOM-8394 -->

*  `StorefrontClickRefundTabCustomerOrderViewActionGroup`.[GitHub-30032](https://github.com/magento/magento2/issues/30032) <!-- ENGCOM-8203 -->

*  `AdminOpenAdminThreeDSecurePageActionGroup`. [GitHub-29845](https://github.com/magento/magento2/issues/29845) <!-- ENGCOM-8115 -->

*  `AdminCustomerClickFirstRowEditLinkActionGroup`  [GitHub-29501](https://github.com/magento/magento2/issues/29501) <!-- ENGCOM-8043 -->

*  `StorefrontClickAddToCartButtonActionGroup`. [GitHub-29823](https://github.com/magento/magento2/issues/29823) <!-- ENGCOM-8113 -->

*  `AdminDeleteTaxRateActionGroup`. [GitHub-29940](https://github.com/magento/magento2/issues/29940) <!-- ENGCOM-8192 -->

*  `AdminOpenWebConfigurationPageActionGroup`. [GitHub-29846](https://github.com/magento/magento2/issues/29846) <!-- ENGCOM-8126 -->

*  `AdminOpenGeneralConfigurationPageActionGroup`. [GitHub-29847](https://github.com/magento/magento2/issues/29847) <!-- ENGCOM-8114 -->

*  `AdminOrderClickSubmitOrderActionGroup` [GitHub-29649](https://github.com/magento/magento2/issues/29649) <!-- ENGCOM-8023 -->

*  `AdminOpenCatalogProductPageActionGroup`. [GitHub-29941](https://github.com/magento/magento2/issues/29941) <!-- ENGCOM-8209 -->

*  `AdminClickInvoiceButtonIntoOrderActionGroup`. [GitHub-25399](https://github.com/magento/magento2/issues/25399) <!-- ENGCOM-8210 -->

*  `AdminGridBulkActionGroup` [GitHub-28324](https://github.com/magento/magento2/issues/28324)<!-- ENGCOM-7334 -->

*  `AdminGridColumnShowActionGroup` [GitHub-28324](https://github.com/magento/magento2/issues/28324)<!-- ENGCOM-7334 -->

*  `AdminOpenIndexManagementPageActionGroup`. [GitHub-29825](https://github.com/magento/magento2/issues/29825) <!-- ENGCOM-8123 -->

*  `AdminOpenCatalogSearchTermIndexPageActionGroup`. [GitHub-29844](https://github.com/magento/magento2/issues/29844) <!-- ENGCOM-8128 -->

*  `AdminClickAddProductToggleAndSelectProductTypeActionGroup` [GitHub-30917](https://github.com/magento/magento2/issues/30917) <!-- ENGCOM-8439 -->

*  `StorefrontCheckoutClickSaveAddressButtonActionGroup`. [GitHub-30916](https://github.com/magento/magento2/issues/30916) <!-- ENGCOM-8454 -->

*  `AdminOpenCurrencyRatesPageActionGroup`. [GitHub-30783](https://github.com/magento/magento2/issues/30783) <!-- ENGCOM-8432 -->

*  `AdminClickGetShippingMethodsAndRatesActionGroup`. [GitHub-30782](https://github.com/magento/magento2/issues/30782) <!-- ENGCOM-8436 -->

*  `AdminSelectFixedShippingMethodActionGroup`. [GitHub-30782](https://github.com/magento/magento2/issues/30782) <!-- ENGCOM-8436 --> 

*  `StorefrontClickProceedToCheckoutActionGroup`. [GitHub-30926](https://github.com/magento/magento2/issues/30926) <!-- ENGCOM-8438 -->

### Newsletter

<!--- MC-38789-->

*  Admin users can now edit a customer account as expected when the customer is subscribed to a queued newsletter. [GitHub-30645](https://github.com/magento/magento2/issues/30645)

<!-- ENGCOM-8034 -->

*  Magento now re-sends newsletter subscription confirmation if the shopper does not confirm their newsletter subscription. [GitHub-28422](https://github.com/magento/magento2/issues/28422)

### Payment methods

<!--- MC-35161-->

*  Payment methods are now loaded in the Admin for all websites as expected in a multi-store deployment.

<!--- MC-36954-->

*  Magento no longer displays the `Purchase Order number is a required field` message above the coupon code field before the shopper enters any information in deployments where Purchase Order has been configured as the only available payment option.

<!--- MC-35161-->

*  Payment methods are now loaded in the Admin for all websites as expected in a multi-store deployment.

<!--- MC-35152-->

*  Magento now completes Payflow Pro payments successfully when the shopper’s name contains accented letters. Previously, payment did not complete, and Magento logged this error: `report.CRITICAL: String to be escaped was not valid UTF-8 or could not be converted`.

#### PayPal

<!--- MC-35692-->

*  Merchants can now successfully place an order from the Admin after switching from a payment method that uses a credit card to a non-credit-card payment method. Previously, when a merchant clicked the **Submit Order** button, the loading process started but never completed, and the order was not placed.

<!--- MC-37649-->

*  Magento no longer creates duplicate orders when an order is placed with PayPal Express. Previously, when a shopper tried to pay for an order with PayPal Express but PayPal returned a 10415 error, Magento still created the order. This resulted in duplicate orders on the merchant’s site. [GitHub-13952](https://github.com/magento/magento2/issues/13952)

<!--- MC-38829-->

*  PayPal Settlement reports are now available at **Reports** > **Sales** > **PayPal Settlement** as expected. Previously, Magento did not list these reports on the PayPal settlement report grid and displayed this message: `We couldn't find any records`.

<!--- MC-39442-->

*  Clicking the **PayPal** button during checkout no longer triggers a redundant `web-api` call. Previously, two requests were triggered, which doubled the charge for the product.

### Performance

<!--- MC-37705-->

*  Performance issues in `module-catalog-import-export/Model/Import/Product/Option.php` have been addressed. The time required to export or import more than 100,000 records has been reduced. See the [Import/Export takes longer than expected with large numbers of product options](https://support.magento.com/hc/en-us/articles/360050695772) Knowledge Base article.

<!-- MC-37816 -->

*  We have improved the performance of scheduled exports of catalogs that include more than 100,000 products using consumers.

<!-- MC-38306 -->

*  Magento no longer flushes category cache when you add or save a disabled product to a category. Previously, Magento flushed the cache for related categories despite the product status, which affected server performance.

<!-- MC-38518 -->

*  Page load time for updating product quantity in the shopping cart has improved. Previously, Magento executed multiple separate queries for each product in shopping cart, which increased page load time.

<!-- MC-39700 -->

*  An indexer has been added to the `Magento_Bulk`  MySQL table, which has improved the performance of bulk operations.

<!-- MC-38593 -->

*  Magento now caches the children IDs of configurable products. This has improved page load performance by reducing the number of database requests. [GitHub-30585 ](https://github.com/magento/magento2/issues/30585)

<!-- MC-37594 -->

*  Loading of the Admin dashboard has been improved. Previously, Magento displayed tab names as a list before the page completed loading.

<!-- MC-37417 -->

*  Redis cache management has been improved by the addition of expiry limits for layout caches. Previously, Redis caches reached allocated maximum memory quickly in large deployments, and Magento threw errors on write operations.

<!-- ENGCOM-8016 -->

*  Checkout performance has been improved by the removal of a redundant database query in `app/code/Magento/Catalog/Model/CategoryLink.php`. [GitHub-29453](https://github.com/magento/magento2/issues/29453)

<!-- ENGCOM-8290 -->

*  `Magento\Framework\DB\Adapter\Pdo\Mysql->isTableExists` has been refactored to improve performance. Redundant calls to `SHOW TABLE STATUS` to check for the existence of a table have been reduced. [GitHub-29662](https://github.com/magento/magento2/issues/29662)

<!-- ENGCOM-8258 -->

`getPageLayoutsConfig` is now saved in cache, which has improved config builder performance. [GitHub-29546](https://github.com/magento/magento2/issues/29546)

### Persistent

<!-- MC-36647 -->

*  Shoppers can no longer place an order after their session cookie has expired when persistent cart is enabled. Instead, Magento displays the login page so that the shopper can log in. Previously, Magento placed the order. Magento did not properly validate the persistent customer when `PHPSESSID`had expired, and `customerSession` was re-created from the persistent information.

<!--- MC-39127-->

*  Magento now displays the Welcome message as expected after a shopper logs into a store where persistent shopping cart is enabled. Previously, Magento displayed the **Not you?** message after logging in.

<!--- MC-38269-->

*  Magento no longer displays the **Not you?** text when a customer selects the **Remember Me** option when logging in to a deployment where persistent shopping cart is enabled.

<!--- MC-37109-->

*  Magento no longer displays the contents of a customer’s cart after the customers session expires. Previously, Magento displayed this error when a guest customer tried to check out when persistent shopping cart was enabled: `No such entity with cartid = 0`.

### Pricing

<!--- MC-34394-->

*  Consecutive asynchronous price updates no longer interfere with each other, and the correct status is assigned to each operation. Previously, if an asynchronous price update failed, all following asynchronous price updates would fail until the corresponding queue consumer was restarted. [GitHub-27865](https://github.com/magento/magento2/issues/27865)

### Reports

<!--- MC-36652-->

*  **Reports** > **Marketing** > **Products in Carts** now displays only the record in the allowed scope of the user who is generating the report. Previously, all data was available for all scopes.

<!--- MC-38925-->

*  **Reports** > **Marketing** > **Products in Carts** now displays only the records in the allowed scope of the user who is generating the report. Previously, all data was available for all scopes.

<!--- MC-38074-->

*  Magento now uses the currency specified in the role scope of the merchant generating the report when displaying product currency in the Products In Cart report.

<!--- MC-37934-->

*  The Recently Viewed and Recently Compared product features now display statistics for different stores and websites in the Admin as expected in a multi-store deployment. Previously, these features did not take into account all stores or websites.

<!--- MC-37217-->

*  Prices in Order reports now use the correct currency symbol.

<!-- ENGCOM-8314 -->

*  Magento now verifies the existence of a token when a user clicks the Admin dashboard **Go to Advanced Report** button.  If the token exists, Magento displays theAdvanced Reporting page. If the token is not configured, Magento displays an informative page in the User Guide. [GitHub-25411](https://github.com/magento/magento2/issues/25411)

### Reviews

<!--- MC-37117-->

*  The New Review page now loads as expected when you click the **New Review** button on Admin **Marketing** > **All Reviews**. Clicking on a product on this page opens the expected new review form for that product.

### Sales

<!--- MC-36219-->

*  The `order_created_at` column of the `sales_shipment_grid` is now updated as expected after each update.

<!--- MC-36405-->

*  You can now successfully re-order a product with a custom options date from a store where **Use JavaScript Calendar** is enabled. Previously, when you tried to re-order, Magento did not add the item to the cart and displayed this error: `Could not add the product with SKU "simp1" to the shopping cart: Please specify date required option(s).`

<!--- MC-36533-->

*  Magento no longer immediately closes an order when a shopper checks out an order that consists of a virtual product with a total cost of $0 in deployments where the zero subtotal checkout method is enabled.

<!--- MC-36755-->

*  Magento no longer archives an order before processing it. Previously, multi-select action on the Admin order grid affected unselected orders.

<!--- MC-37371-->

*  The credit memo grid now displays the correct currency symbol when the Saudi Riyal (SAR) is set as the base currency.

<!--- MC-37880-->

*  Magento now consistently displays shipping address information as expected on the order page during checkout.

<!--- MC-38666-->

*  The value of `total_qty` now matches the value of `total_qty_ordered` in sales invoices.

<!--- MC-38717-->

*  Asynchronous sending of sales emails now sends email for only those orders that were created after the date of the last update. Previously, Magento did not filter emails by date when asynchronous sending was enabled.

<!--- MC-39135-->

*  Magento now sends invoice email as expected when an order is placed from the Admin.

<!--- MC-38917-->

*  Magento now clears existing order data during a session when a merchant creates a new order for a customer from the Admin.

<!--- MC-38915-->

*  You can now change the customer group for new customers that are created through an Admin order when **Enable Automatic Assignment to Customer Group** is enabled. You can also assign customer group based on VAT validation. Previously, when validating the VAT number, the request object did not check the assigned request `group_id`. By default, it used the default `group_id`.

<!--- MC-37539-->

*  Magento no longer changes the status of a custom order status with `Suspected Fraud` status to `Processing` after a merchant creates a partial shipment using the REST API.

### Sales Rule

<!--- MC-34793-->

*  Coupon codes that have been applied based on shipping method are no longer applied when a shopper changes shipping method. Previously, Magento did not clear coupon codes when shoppers switched shipping methods.

<!--- MC-34649-->

*  Shoppers cannot apply a coupon code more frequently than the **Uses Per Customer** setting permits. Previously, if a shopper had multiple browser windows open and placed multiple orders concurrently, each order received the discount, even though the **Uses Per Customer** setting had a value of **1**.

### Search

<!--- MC-35095-->

*  Elasticsearch no longer throws an unknown modifier error when a shopper searches on a search synonym. Previously, escaper was missing an escaping slash symbol in regular expressions, which resulted in a fatal error.

<!--- MC-37577-->

*  Advanced search no longer returns the children of configurable products as individual search results when the child products were configured with visibility set to **Not Visible Individually**.

<!--- MC-37954-->

*  The Elasticsearch sort of product names in search results is no longer case-sensitive.

<!-- ENGCOM-8329 -->

*  The search results page is now cached as expected when the **set Number of top search results to cache to 0** setting is enabled in Admin **Stores**  >  **Configuration**  >  **Catalog**  >  **Catalog**  > **Catalog Search**.

<!--- MC-36807-->

*  The catalog search indexer now executes without throwing an error due to Elasticsearch field limit. Previously, Magento threw this error: `Limit of total fields [xxx] in index [m24dev_product_1_v10] has been exceeded`.

<!--- MC-35491-->

*  The performance of catalog search has improved. Disabling **Enable Search Suggestions** (**Stores** > **Configuration** > **Catalog** > **Catalog Search** ) works as expected. Previously, Magento queried the MySQL `search_query` table instead of Elasticsearch for autocomplete search suggestions. [GitHub-25534](https://github.com/magento/magento2/issues/25534)

<!--- MC-35256-->

*  Elasticsearch now filters product prices the same as MySQL. The field type `price_*`  was changed from `float` to `double` in the Elasticsearch index to improve precision and correct a floating-point error.

<!-- ENGCOM-8393 -->

*  A keydown event listener has been added to the Admin to activate the global search form when a forward slash is entered. [GitHub-29551](https://github.com/magento/magento2/issues/29551)

<!--- MC-24217-->

*  Elasticsearch no longer throws an error but instead displays no products as expected when a `string` value is used to filter products by attribute with an "integer" or "decimal" backend type. Previously, Magento displayed this error in `exception.log`: `number format exception`.

<!-- ENGCOM-8303 -->

*  Elasticsearch no longer throws an exception when a search term contains a  `/`.  [GitHub-25886](https://github.com/magento/magento2/issues/25886), [GitHub-25110](https://github.com/magento/magento2/issues/25110)

*  Search is now disabled as expected for a selected customer group from the products query when the **Disallow Catalog Search By** configuration setting in the general Category Permissions is enabled. [GitHub-29927](https://github.com/magento/magento2/issues/29927)

### Shipping

<!--- MC-38247 -->

*  The checkout process no longer fails when a network interruption disrupts the connection to the DHL shipping method. Instead, Magento displays other available shipping methods. Previously, the checkout process stalled when the connection to DHL shipping was interrupted, and Magento displayed this error: `Sorry, no quotes are available for this order at this time`. [GitHub-29902](https://github.com/magento/magento2/issues/29902)

<!--- MC-35194-->

*  The fields that describe the UPS delivery method on Admin **Stores** >  **Configuration** > **Sales** > **Delivery Methods** are now enabled as expected.

<!--- MC-35633-->

*  Shipments created through the POST `/rest/V1/shipment` endpoint now update orders properly. Previously, Magento created a shipment, but shipment status remained in the processing state.

<!--- MC-37120-->

*  Magento no longer removes simple products from the shopping cart when another product is removed from the cart before checkout with Ship to Multiple Addresses. [GitHub-30259](https://github.com/magento/magento2/issues/30259)

<!--- MC-38031-->

*  The Order Review page now displays the tax amount before shipping amount as expected for orders being shipped to multiple addresses.

<!-- ENGCOM-8257 -->

*  UPS shipment tracking now indicates a status of `Delivered On` only when a package has been delivered. [GitHub-30032](https://github.com/magento/magento2/issues/30032)

<!--- MC-38825-->

*  Magento now displays the correct cart subtotal for orders that contain a virtual product when the shopper navigates back to their cart from checking out with multiple addresses.

<!--- MC-38682-->

*  Merchants can now create a shipping label from the shipping page for an existing order that uses FedEx shipping when JavaScript bundling is enabled. Previously, Magento threw an error when the merchant clicked the **Create Shipping Label** button.

<!--- MC-36953-->

*  The shipment tracking link in the shipment confirmation email sent to customers now works as expected. Previously, this link returned a 404 error.

### Sitemap

<!--- MC-37306-->

*  Sitemaps that are generated by `cron` now include correct image URLs. Previously, the generated cached image path was incorrect in multi-store deployments.

### Store

<!-- ENGCOM-7543 -->

*  The Admin and main store switcher now reflect changes made to the store sort order in the Admin. [GitHub-13401](https://github.com/magento/magento2/issues/13401)

<!-- ENGCOM-8274 -->

*  Magento now creates correct URLs for categories and products after a store view’s top-level URL key is changed. Previously, when a store view’s category tree contained modified  `url_keys`, if a category key did not change but the category parents’ key did, then the original code would used the category ’s default store view when creating URLs. [GitHub-28633](https://github.com/magento/magento2/issues/28633)

### Target rules

<!--- MC-34998-->

*  Loading of product details pages has been optimized. We have added indices for database tables that optimize target rule conditions queries for many cases.

### Tax

<!--- MC-37666-->

*  VAT validation on a guest order no longer results in Magento saving the quote with an incorrect Customer Tax Class. [GitHub-30018](https://github.com/magento/magento2/issues/30018)

<!--- MC-37761-->

*  Orders being shipped to multiple addresses can now be saved during checkout when FPT is configured. Previously, after completing an order for multiple addresses, Magento displayed a blank page instead of the order success page.

### Test

<!--- MC-37364-->

*  `bin/magento dev:tests:run` now launches the following tests as expected: all, unit, integration, integration-all, static, static-all, integrity, legacy, and default.

<!--- MC-38488-->

*  `AdminMediaGalleryInsertLargeImageFileSizeTest` has been refactored.

<!-- ENGCOM-8158 -->

*  Unit tests are now compatible with PHPUnit 8. [GitHub-29779](https://github.com/magento/magento2/issues/29779)

<!-- ENGCOM-8009 -->

*  `\Magento\TestFramework\TestCase\WebapiAbstract` now contains a function that supports comparing large nested arrays of expected and actual outcomes in tests. Irrelevant keys in the outcome can now be ignored. [GitHub-29498](https://github.com/magento/magento2/issues/29498)

<!-- ENGCOM-8024 -->

*  `AdminMediaGalleryCatalogUiEditCategoryGridPageTest` no longer fails randomly. [GitHub-1764](https://github.com/magento/adobe-stock-integration/issues/1764)

<!-- ENGCOM-8041 -->

*  `dev/tests/integration/testsuite/Magento/Customer/Controller/AccountTest` has been improved. (assert is now based on `XPath` selector instead of `assertStringContainsString`.) [GitHub-29700](https://github.com/magento/magento2/issues/29700)

<!-- ENGCOM-8017 -->

*  Added test coverage for the `AdminAnalytics` module. [GitHub-29500](https://github.com/magento/magento2/issues/29500)

<!-- ENGCOM-8266 -->

*  Integration and API functional tests are now compatible with PHPUnit 9.3. [GitHub-30146](https://github.com/magento/magento2/issues/30146)

<!--- MC-35798 -->

*  Corrected issues with the GraphQL `testRequestCacheTagsForCategoryListOnMultipleIds` test. [GitHub-29372](https://github.com/magento/magento2/issues/29372)

<!-- ENGCOM-8327 -->

*  The currency availability test for Company credit has been automated.

### Theme

<!--- MC-37630 -->

*  Design configuration no longer generates DDL operations. Previously, when the design configuration was updated, Magento generated DDL statements that could trigger MySQL errors.

<!-- ENGCOM-8112 -->

*  Redundant code in the `Magento_ConfigurableProduct` module in the backend theme has been removed.  [GitHub-29857](https://github.com/magento/magento2/issues/29857)

<!-- ENGCOM-8144 -->

*  Redundant less styles navigation and unused properties in the Blank theme have been removed. [GitHub-29914](https://github.com/magento/magento2/issues/29914)

<!-- ENGCOM-8285 -->

*  Added collapsible navigation functionality to the Blank theme in mobile view. [GitHub-30237](https://github.com/magento/magento2/issues/30237)

### Translation and locales

<!--- MC-36836 -->

*  The Admin Orders grid date picker grid now works as expected when the Admin locale is Arabic (`ar_SA - Saudi Arabia`).

<!--- MC-38476 -->

*  Magento no longer displays an error message when a shopper enters an Argentinian address with a valid post code when registering or adding a new address. Previously, Magento displayed this error: `Provided Zip/Postal Code seems to be invalid. Example: 1234. If you believe it is the right one you can ignore this notice.`

<!--- MC-38663-->

*  Magento no longer throws an error when a shopper enters a five-digit postal code for a Korean address.

<!-- ENGCOM-8244 -->

*  Added support for Uruguay regions that are defined in [ISO 3166-2:UY](https://en.wikipedia.org/wiki/ISO_3166-2:UY). [GitHub-29729](https://github.com/magento/magento2/issues/29729)

<!-- ENGCOM-8220 -->

*  `zip_codes.xml` has been updated to enforce eight-digits for Brazilian zip codes. [GitHub-29984](https://github.com/magento/magento2/issues/29984)

<!-- ENGCOM-8304 -->

*  Improved localization of remaining unlocalized phrases. [GitHub-11175](https://github.com/magento/magento2/issues/11175)

<!-- ENGCOM-8380 -->

*  The grid search input placeholder can now be translated. [GitHub-30510](https://github.com/magento/magento2/issues/30510)

### UI

<!--- MC-38509-->

*  The **Create an Account** button on the Create New Account page remains active when a shopper enters invalid data. Previously, this button was disabled, which prevented shoppers from re-attempting to create an account after making an error. This was a known issue in Magento 2.4.1. [GitHub-30513](https://github.com/magento/magento2/issues/30513)

<!--- MC-38698-->

*  Loading of the shipping grid on the Admin Order Edit page has been improved.

<!--- MC-37870-->

*  Magento now displays the  **Same As Billing Address** check box as expected on the order page when products have been added the cart by SKU.

<!-- ENGCOM-8007 -->

*  The CSS class that defined limited width is now applied as expected to the **Start Time** fields on Admin **Store**  >  **Configuration**  >  **Catalog**  >  **XML Sitemap**  >  **Generation Settings**.  [GitHub-29496](https://github.com/magento/magento2/issues/29496)

<!-- ENGCOM-7992 -->

*  Corrected display issues with the Terms and Conditions checkbox label.  [GitHub-24060](https://github.com/magento/magento2/issues/24060)

<!-- ENGCOM-7948 -->

*  Magento no longer displays the CSS code for a tier price block on the product page when the tier prices are not available. [GitHub-29194](https://github.com/magento/magento2/issues/29194)

<!-- ENGCOM-8084 -->

*  The position of the buttons on the image view details page have been re-ordered to conform with user interface guidelines.  [GitHub-1783](https://github.com/magento/adobe-stock-integration/issues/1783)

<!-- ENGCOM-8342 -->

*  Coupon code text field is now displayed in proper width in Internet Explorer/EDGE browsers.

<!-- ENGCOM-7630 -->

*  The `@button__border-radius` variable is now defined in the `lib/web/css/source/lib/variables/_buttons.less` library.  `border-radius` has a default value of `3px`. Previously, `border-radius` was hard-coded.  [GitHub-28674](https://github.com/magento/magento2/issues/28674)

<!-- ENGCOM-8067 -->

*  The submit search button (magnifying glass) in the mini search field is now disabled until the minimum search string length has been reached. [GitHub-29704](https://github.com/magento/magento2/issues/29704)

<!--- MC-38807-->

*  The **Preview Template** button now works as expected in the Edit Queue page.

<!--- MC-31892-->

*  Magento now preserves an attribute’s value when you move the attribute from one group to another.

<!-- ENGCOM-8085 -->

*  Added a font weight heavy variable to `lib/web/css/source/lib/variables/_typography.less`. [GitHub-29778](https://github.com/magento/magento2/issues/29778)

<!-- ENGCOM-8211 -->

*  Filter visibility now works with column visibility as expected in Admin grids.  [GitHub-30345](https://github.com/magento/magento2/issues/30345)

### Vault

<!--- MC-39109-->

*  The Vault module now recognizes payment method codes from the request for the payment information management service. Previously, when a shopper placed an order using a saved Braintree credit card, Magento threw this error even when a valid payment method was used: `The requested Payment Method is not available`.

<!-- ENGCOM-7977 -->

*  The banner that Magento displays on the Admin Login as Customer page now remains at the top of the page when the user scrolls. [GitHub-29354](https://github.com/magento/magento2/issues/29354)

### Vertex

*  Address suggestions are now removed as expected when an address is modified.

*  A race condition that prevented some customers from saving their address in their account panel has been resolved.

*  Vertex address validation no longer adds the Address Edit page to the full-page cache in certain conditions.

*  Vertex-calculated tax is now considered when free shipping is configured for an amount inclusive of tax.

### Web API framework

<!--- MC-23904 -->

*  You can now use the REST API to refund an invoice that has a zero quantity of products and zero shipping charges (for example, {“items": [{"qty": 0, "orderItemId": 6, "extensionAttributes": {}}], "appendComment": false, "notify": true, "isOnline": true, "arguments": {"adjustment_negative": 0.0, "adjustment_positive": 0.99, "shipping_amount": 0}}.) Previously, Magento threw this error: `You can't create a creditmemo without products`.

<!--- MC-33732 -->

*  You can now use POST `http://&lt;domain&gt;/rest/V1/categories/` to create or update a category. Previously, Magento did not save the value if the `default_sort_by` value was set as an array. When the `default_sort_by` value was set as a string, Magento threw this error: `Error occurred during \"custom_attributes\" processing. Attribute \"default_sort_by\" has invalid value. The \"string\" value's type is invalid. The \"string[]\" type was expected. Verify and try again.`

<!--- MC-35740 -->

*  Using POST `/rest/V1/invoices/{id}/capture` to capture payment information now works as expected. Previously, Magento authorized the order but captured it only on the payment gateway's site.

<!--- MC-37794 -->

*  You can now use the REST API to correctly create a partial shipment of an order. Previously, using `rest/V1/order/{order_id}/ship` returned the wrong number of shipped products.

<!--- MC-36830-->

*  The `rest/all/V1/categories` and `rest/all/V1/categories?rootCategoryId=2` calls now return populated `name` and `product_count` fields as expected for all categories in the tree. Previously, the category field values were empty. The table name resolver plugin returned an incorrect table name for fetching the count of products by category.

### Wishlist

<!--- MC-33626-->

*  Shoppers can now add a product to a wishlist when the product is assigned to a custom inventory source. [GitHub-3018](https://github.com/magento/inventory/issues/3018)

<!--- MC-35416-->

*  Administrators can now access the Manage Shopping Cart page from the Admin customer page after a customer has added a product to their wishlist from the storefront. Previously, Magento displayed the following error when the administrator clicked the **Manage Shopping Cart** button: `An error has occurred. See error log for details`.

<!--- MC-35573-->

*  The **Add to cart** button on the shared wishlist page now works as expected for anonymous, guest, and users who are not logged in.

<!-- ENGCOM-8062 -->

*  Magento now displays selected configurable product attribute options in the wishlist page as expected.  [GitHub-24091](https://github.com/magento/magento2/issues/24091),  [GitHub-22503](https://github.com/magento/magento2/issues/22503)

## Known issue

**Issue**: Discounts for a specific payment method persist during checkout for a purchase order even when the buyer changes payment method during final checkout. As a result, customers may receive a discount that they are not entitled to. This occurs because a cart rule for the original payment method is still applied despite the change in payment method. **Workaround**: None. <!-- KB-827 -->

## Community contributions

We are grateful to the wider Magento community and would like to acknowledge their contributions to this release. Check out the following ways you can learn about the community contributions to our current releases:

*  If a community member has provided a fix for this release, we identify the fix in the Fixed Issue section of these notes with the phrase, "*Fix provided by community member*".

*  The Magento Community Engineering team [Magento Contributors](https://magento.com/magento-contributors) maintains a list of top contributing individuals and partners by month, quarter, and year. From that Contributors page, you can follow links to their merged PRs on GitHub.

### Partner contributions

The following table highlights contributions made by Partners. This table lists the Partner who contributed the pull request, the external pull request, and the GitHub issue number associated with it (if available).

{% include release-notes/engcomm-2-4-2-partner.md %}

### Individual contributor contributions

The following table identifies contributions from our community members. This table lists the external pull requests, the GitHub issue number associated with it (if available), and the community member who contributed the pull request.

{% include release-notes/engcomm-2-4-2-issues.md %}

### System requirements

Our technology stack is built on PHP and MySQL. For more information, see [System Requirements]({{site.baseurl}}/system-requirements.html).

### Installation and upgrade instructions

You can install Magento Open Source 2.4.2 using [Composer]({{ page.baseurl }}/install-gde/composer.html).

## Migration toolkits

The Data Migration Tool helps transfer existing Magento 1.x store data to Magento 2.x. This command-line interface includes verification, progress tracking, logging, and testing functions. For installation instructions, see [Install the Data Migration Tool]({{page.baseurl}}/migration/migration-tool-install.html). Consider exploring or contributing to the [Magento Data Migration repository](https://github.com/magento/data-migration-tool).

The [Code Migration Toolkit](https://github.com/magento-commerce/code-migration) helps transfer existing Magento 1.x store extensions and customizations to Magento 2.x. The command-line interface includes scripts for converting Magento 1.x modules and layouts.