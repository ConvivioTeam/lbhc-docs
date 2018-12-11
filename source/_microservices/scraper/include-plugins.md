## Plugins

The scraper microservice is built for adding plugins.

Scraper plugins are built with an Object Oriented architecture, so that a scraper plugin is registered if it `extends ScraperPlugin` base class.

Every scaper plugin class must `extends ScraperPlugin` in order to be recognised by the microsservice. Extenstions of this base class must 

1) have the `$name` property set in each plugin.
2) implement a `public function boot()` method.

For example:

```php
class MyExampleScraperPlugin extends ScraperPlugin
{
    /**
     * The Plugin Name.
     *
     * @var string
     */
    public $name = 'my_example_scraper';

    /**
     * Boot-time commands.
     */
    public function boot() {
        // Do something.
    }

    …
}
```

The `boot()` method is called at boot time, and can be used to implement a number of tasks. For example, the `ScraperPlugin` abstract class includes a method to `enableRoutes()` that will look for a `routes.php` file in the root of the scraper plugin that defines any routes for the scraper.

```php
    /**
     * Enable routes for this plugin.
     *
     * @param string $path
     */
    protected function enableRoutes($path = 'routes.php')
    {
        $this->app->router->group(
            ['namespace' => $this->getPluginControllerNamespace()],
            function ($router) use ($path) {
                require $this->getPluginPath() . DIRECTORY_SEPARATOR . $path;
            }
        );
    }
```

## Base plugin sets

There are thus two basic plugin sets. Each is an abstract base class, so that it can be extended for a particular source, for example, where a different authentication key or method is required for access.

These base plugins are found in `namespace App\Plugins` in `./source/app/Plugins`. These plugins search for implementations in `namespace App\Scraper` in `./source/app/Scraper`.

### 1. [Web Page scrapers](./webpage)

These are scrapers that make an HTTP GET request for a web page and then parse the page content to find the specific element on the page, e.g. using a CSS selector.


### 2. [API scrapers](./api)

These are scrapers that make HTTP GET (and possibly POST requests) for API resource endpoints and retrieve JSON (or XML) data in response.
