yii-gearman
===========

gearman wrapper for yii framework

Usage 
=====
Extract the files into the extension directory and change the config like bellow:
```php
'components' => array(
        'gearman' => array(
            'class' => 'ext.Gearman',
            'servers' => array(
                array('host' => '127.0.0.1', 'port' => 4731),
            ),
        ),
    )
```
Simple example:
```php
// Client example
Yii::app()->gearman->client()->doBackground("reverse", "Hello world!");
 
// Worker example
 
function reverse($job)
{
    return strrev($job->workload());
}
 
Yii::app()->gearman->worker()->addFunction("reverse", array($this, 'reverse'));
while($worker->work()) { echo "Done!"; }
```
