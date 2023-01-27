# DI
Dependacy Injection, Dagger2, Hilt Study material.

## Dependacy injection

- efficient testing
- code extensibility
- single responsibility
- code reusability

## Dagger
- dagger is a fully static, compile-time dependacy injection framework
- compile time checking is performed if dagger can create the required object
- annotation based

- dagger will behave as a system for us to create required objects
- dagger will help us inject these objects
- dagger will manage the lifetime of the objects
- dagger will help us write manageable code

## concepts
- consumer- (@Inject)
- producer- (@Module,@Provides,@Binds)
- connecter- (@Component)

## signleton
- just one instace ie, single object for the whole application
- HTTP client, database connection etc.
