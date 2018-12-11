---
layout: default
title: API scraper
parent: Scraper
grand_parent: Microservices
category: scraper
has_children: true
nav_order: 3
permalink: microservices/scraper/api
---

# API scraper

The API page scraper is a plugin with a set of abstract classes. It is designed as a base scraper with tools that are useful to every scraper that needs to use an API (as opposed to a website) as is data source.

## Base abstract class, ApiScraper

The ApiScraper defines a base scraper class for web pages.

```php
abstract class ApiScraper extends ScraperPlugin implements ApiScraperInterface
{
    ...
}
```

Each individual source scraper should then `extends ApiScraper` to be identifiable and able to function as an API scraper.

### Example

```php
<?php

namespace App\Scraper\ICareOpenObjectsScraper;

use App\Plugins\ApiScraper\Scraper\ApiScraper;

/**
 * A scraper for iCare Open Objects.
 *
 * @package App\Scraper\iCareOpenObjectsScraper
 */
class iCareOpenObjectsScraperPlugin extends ApiScraper
{
    ...
}
```

## API scrapers

{% include scrapers_list.html %}