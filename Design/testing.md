# Testing

Don’t unit test methods that return void, you’re adding nothing other than making refactoring more difficult. If it returns void, you need an integration test.
