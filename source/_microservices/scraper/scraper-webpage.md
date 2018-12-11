---
layout: default
title: Web page scraper
parent: Scraper
grand_parent: Microservices
category: scraper
has_children: true
nav_order: 3
permalink: microservices/scraper/webpage
---

# Web page scraper

The web page scraper is a plugin with a set of abstract classes. It is designed as a base scraper with tools that are useful to every scraper that needs to use a website (as opposed to an API) as is data source.

## Base abstract class, WebPageScraper

The WebPageScraper defines a base scraper class for web pages.

```php
<?php

abstract class WebPageScraper extends ScraperPlugin implements WebPageScraperInterface
{
    ...
}
```

Each individual web page source scraper should `extends WebPageScraper` to be identifiable and able to function as a web page scraper.

### Example

```php
<?php

namespace App\Scraper\ICareWebPageScraper;

use App\Plugins\WebPageScraper\Scraper\WebPageScraper;

/**
 * A scraper for the Hackney iCare website.
 *
 * @package App\Scraper\ICareWebPageScraper
 */
class ICareWebPageScraperPlugin extends WebPageScraper
{
    ...
}
```


## Web page scrapers

{% include scrapers_list.html %}