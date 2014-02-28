---
layout: page
title: Configuration
---

All Samza jobs have a configuration file that defines the job. A very basic configuration file looks like this:

```
# Job
job.factory.class=samza.job.local.LocalJobFactory
job.name=hello-world

# Task
task.class=samza.task.example.MyJavaStreamerTask
task.inputs=example-stream

# Serializers
serializers.registry.json.class=samza.serializers.JsonSerdeFactory

# Systems
systems.example-system.samza.consumer.factory=samza.stream.example.ExampleConsumerFactory
```

There are four major sections to a configuration file. The job section defines things like the name of the job, and whether to use the YarnJobFactory or LocalJobFactory. The task section is where you specify the class name for your StreamTask. It's also where you define what the input streams are for your task. The serializers section defines the classes of the serdes used for serialization and deserialization of specific objects that are received and sent along different streams. The system section defines systems that your StreamTask can read from. Usually, you'll define a Kafka system, if you're reading from Kafka, although you can also specify your own self-implemented Samza-compatible systems. See the hello-samza example project's Wikipedia system for a good example of a self-implemented system.

### Required Configuration

Configuration keys that absolutely must be defined for a Samza job are:

* job.factory.class
* job.name
* task.class
* task.inputs

### Configuration Keys

A complete list of configuration keys can be found on the [Configuration Table](configuration-table.html) page.

## [Packaging &raquo;](packaging.html)
