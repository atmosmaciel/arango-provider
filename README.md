Simple Arango Provider Service for Silex Skeleton
===

Objectivates simplify usage of ArangoDB PHP classes creating less code using a factory.

Usage:
====

private/config.json
=====

```
{
	...
	"arango": {
        "host": "127.0.0.1",
        "port": 8529,
        "user": "app_user",
        "pass": "app_user_pwd",
        "database": "your_database"
    }
	...
}
```

bootstrap
=====

```
$app->register(new \ArangoProvider\Service\Provider());
```

Controller action
=====

To get a cursor from collection handler

```
	$cursor = $app['adb-h']->handleCollection()->get('your_collection');
  
  ...

  return new JsonResponse($cursor,200);
```

To get one collection

```
	$statement = $app['adb-h']->newReadStatement('FOR f IN your_collection
    RETURN
      f
   ');

  $cursor = $statement->execute();
  
  ...

  return new JsonResponse($cursor,200);
```