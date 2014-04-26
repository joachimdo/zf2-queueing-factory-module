zf2-queueing-factory-module
===========================
> This module only provides an abstract factory in order to give access to the queueing functionalities via zend framework 2 service manager.
> For now, it is limited to activemq.

## Installation

Just add QueueAdapters to the listed module names, rename and copy the module.queue-adapters.local.php.dist to your application config, e.g. :

```php
return array (
		"queue-adapters" => array(
				//inform the controller plugin, 
				// "default" =>"activemq",
				"activemq" => array (
						//"host" => "127.0.0.1",
						//"port" => "61613",
						// "scheme" => "tcp",
						
				)
		)

);```


## Usage

An instance of ZendQueue\Queue with the ActivMQ adapter is now available :

* either as a service 

```php
$service = $this->getServiceLocator()->get("activemq");
//write to queue
$service->createQueue("test");
$service->send("Hello World n°1");
//read from queue
$iterator=$service->receive();
$current=$iterator->current();
```

* or as a plugin manager if you are in a Controller

```php
//write to queue
$this->queue()->createQueue("test");
$this->queue()->send("Hello World n°1");
//read from queue
$iterator=$this->queue()->receive();
$current=$iterator->current();
```



 
