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

### Base plugin sets

There are thus two basic plugin sets. Each is an abstract base class, so that it can be extended for a particular source, for example, where a different authentication key or method is required for access.

These base plugins are found in `namespace App\Plugins` in `./source/app/Plugins`. These plugins search for implementations in `namespace App\Scraper` in `./source/app/Scraper`.

#### 1. [Web Page scrapers](./webpage)

These are scrapers that make an HTTP GET request for a web page and then parse the page content to find the specific element on the page, e.g. using a CSS selector.


#### 2. [API scrapers](./api)

These are scrapers that make HTTP GET (and possibly POST requests) for API resource endpoints and retrieve JSON (or XML) data in response.

### Plugin architecture

Each plugin includes an abstract scraper class that itself `extends ScraperPlugin`. This abstract class can then be implemented by Scrapers to define the kind of scraper they are and give them access to base toolkits. For example:

```php
namespace App\Plugins\WebPageScraper\Scraper;

...

abstract class WebPageScraper extends ScraperPlugin { ... }
```

Classes that extend a plugin Scraper class are then defined as Scraper plugins. For example:

```php
namespace App\Scraper\ICareWebPageScraper;

...

class ICareWebPageScraperPlugin extends WebPageScraper { ... }
```

Inside each plugin's `./Http` directory are the abstract tools for HTTP request/repsonse handling for each source type, API and web page.

### Drivers and Services

To support HTTP request/response handling, a scraper needs an HttpDriver and an HttpService.

#### HttpDrivers

An `HttpDriver` uses [Guzzle](http://docs.guzzlephp.org/en/stable/) to contruct GET requests to fetch data from a remote source. (In principle a driver could make POST, PUT and DELETE, though those are not currently implemented.) HttpDrivers also use Guzzle to handle the responses and return them to the original call.

HttpDrivers are created with a configuration array passed to the constructor. HttpDrivers **require a base URL** in the configuration array.

Given that the response from an API and a web page are different (json or XML for the former, markup for the latter), the responses need to be handled differently, turning them into a usable response result class.

#### HttpServices

An `HttpService` creates the definition of how a specific scraper should connect to the remote source. It holds the necessary properties for making a connection, such us:

- the `HttpDriver` to use
- connection configurations, including the path to the remote source

It includes methods to:

- contruct the URL for an HTTP request
- get the response from the request

It also includes methods that are shortcuts for making specific HTTP requests and handling a request-specific response. These shortcut methods require a Request object, which defines any required or optional parameters. The method should return a Respone object appropriate to the request. For example, a simple method for 'hello' request that checks the base URL is valid might look like:

```php
    /**
     * Make a simple request for the API hello endpoint.
     *
     * @param \App\Http\Request\GetHelloRequest $request
     *   GetHelloRequest object.
     *
     * @return \App\Plugins\WebPageScraper\Http\Response\HelloWebPageResponse
     *   Hello response object.
     *
     * @throws
     */
    public function hello(GetHelloRequest $request)
    {
        $this->setUrl('/');
        return new HelloWebPageResponse($this->getDriver()->get($this->getUrl(), $request));
    }
```

To make a 'hello' request, to check a site is up, then, you would need to first get a HttpDriver, pass it to a HttpService, get a GetHelloRequest object and then call the shortcut method:

```php
$driver_conf = ['some', 'configuration', 'here'];
$driver = new MyWebPageHttpDriver($driver_conf);

$service_conf = ['some', 'other', 'configuration', 'here'];
$service = new MyWebPageHttpService($driver, $service_conf);

$request = new GetHelloRequest();
$response = $this->hello($request);
```
