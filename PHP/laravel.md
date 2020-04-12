
# Laravel

## Design

When requiring dependencies for custom Laravel validation rules that are instantiated in a static method, it may be more elegant and equally testable to use the application facade to make the rule rather than building the dependencies manually. Likewise the request facade might be suitable in transformers.

Only use events in an application if they genuinely provide an opportunity to decouple. It will be obvious if you can’t genuinely decouple because you will want to use the event name in the listener name.

If your event listener is always going to be tied to a particular event, use an action instead. Ideally actions would always be unit testable, but if using Active Record that’s likely to be difficult.

## Gotchas

### Caching

When using Laravel’s cache tags, it’s necessary to use the same tags for all subsequent calls into the cache

### Config

When making a change to Laravel config, the queue worker must be restarted for the change to affect the queued processes

Laravel’s config helper cannot be used from inside config files. If you want to split config across multiple files but provide a single entrypoint, you have to include the files manually.

### Eloquent

Attempting a join on an Eloquent model query can cause very confusing results if there are columns with the same name (‘id’ being the most likely culprit). Joins should only be used when not returning models, e.g. for reporting. Otherwise with or whereHas are likely to be what you want.

Be very wary of using Eloquent observers and model events when that event is taking place as part of a database transaction. They will be fired immediately.

Be very wary of using Eloquent observers and model events when firing queued listeners. You don’t get any control over the serialization in Laravel 5.3

Don’t use factories to create models from inside other factories except in an “after” hook. Laravel factories do not apply attribute overrides before making the original object, so you can get unexpected results and lots of orphans

Eloquent now (v > 5.7 ?) only throws a `MassAssignmentException` if the attribute is marked guarded. If it just isn’t fillable the attribute gets silently ignored when fill() is used

When setting a default Eloquent model attribute for a JSON column that is cast to an array, remember to provide the default as a string instead of an array

### Testing

Test data providers run before Laravel is bootstrapped, so it isn’t possible to use any Laravel classes there

By default, Laravel tests using the `WithoutMiddleware` trait cannot test routes that use route model bindings because the trait prevents the `SubstituteBindings` middleware from running

### Validation

When validating dates in laravel, always use the date_format rule rather than the date rule, as models don’t use Carbon::parse by default when setting date attributes

Laravel runs “after” validation hooks even if the main validation rules fail, which can cause some odd errors

Laravel’s FormRequest does not extend the main request, but are instantiated from it. This can lead to input merged in middleware to go missing. Use the app “resolving” hook in a service provider to merge it in instead if appropriate.

### Tips

When testing Laravel database persistence, you can test for an exact JSON match on a column by casting the JSON encoded test value as follows: `CAST('{$json}' AS JSON)`

When checking for the existence of a related model on an Eloquent model that has the relationships eager loaded, the way to go is to use the relationLoaded() method and then is_null to check existence. E.g. `$application->relationLoaded(‘course’) && !is_null($application->course)`. Or maybe just is_null if you’re absolutely certain the relation has been eager loaded.

I don’t know how, but Eloquent is able to apply attribute accessors when using pluck to fetch a single column from the database

It’s possible to mock Eloquent model attributes and relation values by mocking the underlying getAttribute() method. Likewise the request can be mocked using the offsetExists and offsetGet methods

It’s pretty easy to create custom Eloquent model events by providing a static method that calls the registerModelEvent() function with a new event name. That method can then be called from the model’s boot function or a service provider to register event listeners. The event is fired by calling the fireModelEvent method.

It’s possible to test routes that leverage Laravel Cashier to make requests to the Stripe API by mocking the Stripe PHP client library’s HTTP client class and overriding the client in the base Stripe class
