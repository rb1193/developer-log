# Libraries

## Carbon

Carbon object add and subtract methods don’t return a fresh instance

## Guzzle

When debugging API calls made using Guzzle, which usually truncates the error message in the log, catch the exception and use `$e->getResponse()->getBody()->getContents()` to see what the hell is going on. However, it seems to be possible for getResponse() to return null when the request fails.

## Mockery

Constructor parameters can be passed to Mockery using `\Mockery::mock(Mockable::class, array($param));`

## PHPUnit

In PHPUnit, you can use the @doesNotPerformAssertions test to simply run a method and test it does not throw an exception without the test being marked ‘risky’

When testing multiple similar cases, consider using a data provider to populate the test fixture. Particularly good for testing validation and authorization
