# Testing

Don’t unit test methods that return void, you’re adding nothing other than making refactoring more difficult. If it returns void, you need an integration test.

When building SPAs, making use of separate routes as much when possible can help keep your components small and testable

When unit testing a pure function with pure functional dependencies that require complex setup, instead of mocking to avoid the setup, call the dependency function instead when building the assertion. That way, if you make an internal change to the dependency, you don't break your tests, but you've also avoided mocking, which is good because mocking can prevent you from finding out if you've broken a contract.