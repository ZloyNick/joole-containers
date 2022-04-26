# Joole Containers

**Joole Containers** is a library for storing objects. At its core, it is an implementation of PSR-12 and its complement.

## Getting started

* Install it with using composer:
<code>
composer require zloynick/joole-containers
</code>

## Using

* Create a container object:
<pre>
<code>
use joole\containers\Container;

$container = new Container();
...
</code>
</pre>

* Register your object to created container:
<pre>
...
class MyCustomPeople{

    private string $age;
    private string $name;

    public function __construct(
        $name,
        $age
    )
    {
        $this->name = $name;
        $this->age = $age;
    }

    public function getName(): string
    {
        return $this->name;
    }

}

$container->register(MyCustomPeople::class, ['name' => 'Alex', 'age' => 22]);
...
</pre>

Now we can use the object from the container
<pre>
<code>
...
echo $container->get(MyCustomPeople::class)->getName();// Alex
...
</code>
</pre>

## Addition functional

* You can get number of object in container: <code>$count = count($container);</code>
* Multiple push: 
<pre>
<code>
$container->multiplePush(['param1' => [1, 2, 3], 'param2' => new stdClass()], Class1::class, Class2::class);
</code>
</pre>

**Note:** *the keys of the array of parameters must correspond to the name of the variables of the constructor classthe keys of the array of parameters must correspond to the name of the variables of the constructor class.*
