---
layout: default
title: Event Sourcing
parent: Data Store
grand_parent: Microservices
has_children: false
nav_order: 1
permalink: microservices/datastore/eventsourcing
---

# Data Store: Event Sourcing

The Data Store microservice is built with [Laravel Lumen](https://lumen.laravel.com). It is a small PHP application.

The Data Store microservice uses [Laravel queues in Lumen](https://lumen.laravel.com/docs/5.7/queues) to source jobs from the [event store microservice]({% link _microservices/eventstream/index.md %}).

## Apache Kafka integration

The Data Store uses a [Kafka Queue driver for Laravel](https://github.com/rapideinternet/laravel-queue-kafka) to source events from Apache Kafka. The driver library includes a Laravel service provider to create queue jobs sourced from events in Kafka.

The following is included in `bootstrap/app.php`:

```php
$app->register(Rapide\LaravelQueueKafka\LumenQueueKafkaServiceProvider::class);
```

### Kafka queue configuration

The app must be configured correctly for the Laravel queue service provider to connect to Kafka.

Consequently, there is copy the whole of `{vendor_path}/laravel/lumen-framework/config/queue.php` at `config/queue.php`.

Secondly, the file `config/kafka.php` extends the queue configurations with the following contents:

```php
<?php
/**
 * Kafka queue connection config.
 */

return [
    'connections' => [
        'kafka' => [
            'driver' => 'kafka',
            'queue' => env('KAFKA_QUEUE', 'store'),
            'consumer_group_id' => env('KAFKA_CONSUMER_GROUP_ID', 'dos_data_store'),
            'brokers' => env('KAFKA_BROKERS', 'localhost'),
            'sleep_on_error' => env('KAFKA_ERROR_SLEEP', 5),
            'sleep_on_deadlock' => env('KAFKA_DEADLOCK_SLEEP', 2),
        ],
    ],
];
```

The values will be populated from the environment variables.

## Running the queue worker

 The [queue worker](https://laravel.com/docs/5.7/queues#running-the-queue-worker) must be running for the Data Store to source events and create jobs.

{: .alert .alert-info }
Since queue workers are long-lived processes, they will not pick up changes to your code without being restarted. So, the simplest way to deploy an application using queue workers is to restart the workers during your deployment process.

You may gracefully restart all of the workers by issuing the queue:restart command:

```bash
php artisan queue:restart
```

### In production

To keep the `queue:work process` running permanently in the background, you should use a process monitor such as [Supervisor](https://laravel.com/docs/5.7/queues#supervisor-configuration) to ensure that the queue worker does not stop running.

### In local development

In local development, you can get a shell inside the PHP container easily:

```bash
make shell
```

Once inside a shell on the PHP container, move into the correct directory and run the queue worker:

```bash
cd ./source
php artisan queue:work kafka
```

{: .alert .alert-info }
Note that once the `queue:work` command has started, it will continue to run until it is manually stopped or you close your terminal.
