## Scraping a Source

Each scraper makes HTTP requests for data from a source system, whether an API or a website. To do that it needs 2 key elements to make requests and handle the responses:

1) an HTTP request/response driver
2) an HTTP request service

### HTTP Drivers

There is a base `HttpDriver` class that extends an `AbstractHttpDriver`. This has some 