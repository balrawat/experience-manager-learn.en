---
title: Sitemaps
description: Learn how to help boost your SEO by creating sitemaps for AEM Sites.
version: Cloud Service
feature: Core Components
topic: Content Management
role: Developer
level: Intermediate
kt: 9165
thumbnail: 337960.jpeg
exl-id: 40bb55f9-011d-4261-9f44-b1104a591252
---
# Sitemaps

Learn how to help boost your SEO by creating sitemaps for AEM Sites.

>[!VIDEO](https://video.tv.adobe.com/v/337960/?quality=12&learn=on)

## Resources

+ [AEM Sitemap Documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/seo-and-url-management.html?lang=en#building-an-xml-sitemap-on-aem)
+ [Apache Sling Sitemap documentation](https://github.com/apache/sling-org-apache-sling-sitemap#readme)
+ [Sitemap.org Sitemap documentation](https://www.sitemaps.org/protocol.html)
+ [Sitemap.org Sitemap index file documentation](https://www.sitemaps.org/protocol.html#index)
+ [Cronmaker](http://www.cronmaker.com/)

## Configurations

### Sitemap scheduler OSGi configuration

Defines the [OSGi factory configuration](http://localhost:4502/system/console/configMgr/org.apache.sling.sitemap.impl.SitemapScheduler) for the frequency (using [cron expressions](http://www.cronmaker.com)) sitemaps will be re/generated and cached in AEM. 

`ui.config/src/main/jcr_content/apps/wknd/osgiconfig/config.publish`

```json
{
  "scheduler.name": "WKND Sitemaps",
  "scheduler.expression": "0 0 2 1/1 * ? *",
  "searchPath": "/content/wknd"
}
```

### Dispatcher allow filter rule

Allow HTTP requests for the sitemap index and sitemap files.

`dispatcher/src/conf.dispatcher.d/filters/filters.any`

```
...

# Allow AEM sitemaps
/0200 { /type "allow" /path "/content/*" /selectors '(sitemap-index|sitemap)' /extension "xml" }
```

### Apache webserver rewrite rule

Ensure `.xml` sitemap HTTP requests are routed to the correct underlying AEM page. If URL shortening is not used, or Sling Mappings are used to achieve URL shortening, then this configuration is not needed.

`dispatcher/src/conf.d/rewrites/rewrite.rules`

```
...
RewriteCond %{REQUEST_URI} (.html|.jpe?g|.png|.svg|.xml)$
RewriteRule ^/(.*)$ /content/${CONTENT_FOLDER_NAME}/$1 [PT,L]
```
