## Plugins

The scraper microservice is built for adding plugins.

Scraper plugins are built with an Object Oriented architecture, so that a scraper plugin is registered if it `extends ScraperPlugin` base class.

There are thus two basic plugin sets. Each is an abstract base class, so that it can be extended for a particular source, for example, where a different authentication key or method is required for access.

### 1. Web Page scrapers

These are scrapers that make an HTTP GET request for a web page and then parse the page content to find the specific element on the page, e.g. using a CSS selector.

```php
<?php

abstract class WebPageScraper extends ScraperPlugin implements WebPageScraperInterface
{
    ...
}
```

Each individual source scraper should then `extends WebPageScraper` to be identifiable and able to function as a web page scraper.

### 2. API scrapers

These are scrapers that make HTTP GET (and possibly POST requests) for API resource endpoints and retrieve JSON (or XML) data in response.

```php
abstract class ApiScraperPlugin extends ScraperPlugin implements ApiScraperInterface
{
    ...
}
```

Each individual source scraper should then `extends ApiScraper` to be identifiable and able to function as an API scraper.