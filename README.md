# DI
Dependacy Injection, Dagger2, Hilt Study material.

## Dependacy injection

- efficient testing
- code extensibility
- single responsibility
- code reusability

- field injection - Field injection is used to set value object as dependency to the field of an object.
- contructor injection - Constructor Injection is the act of statically defining the list of required Dependencies by specifying them as parameters to the class's constructor.

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

## Hilt
- buit on the top of dagger
## application class

```
@HiltAndroidApp
class MyApplication : Application() {....}
```
- newly define application class must be mention in android manifest.
- Application class is a base class of all classes. 
```
## @AndroidEntryPoint
class MyActivity : AppCompactActivity() {.....}
```
### Hilt support following classes
- Application (using @HiltAndroidEntryPoint)
- Activity
- Fragment
- View
- Service
- BroadcastReciever

- if you annotate fragment as a AndroidEntryPoint, you also have to annotate Base activity as an AndroidEntryPoint in which fragment is loaded.
- AndroidEntryPoint generate Hilt Compoenet for each class in your project
``` 
@AndroidEntryPoint
class MyActivity : AppCompactActivity() {...}

//field Injection
@Inject lateinit var Analytics : AnalyticsAdapter
```
## Hilt Binding
- how to provide instaces of class 
- how to create object to inject
```
//constructor injection
class AnalyticsAdapter @Inject constructor(
private var service : AnalyticsService)
{...}
```
## Hilt components

- @Module -it informs hilt to provide instace of certain type.- Hilt module provide implementation of object
- @Bind - @Binds annotation tells Hilt which implementation to use when it needs to provide an instance of an interface.
- @Provides - @Provides in Hilt modules to tell Hilt how to provide types that cannot be constructor injected.
- @InstallIn -  @InstallIn annotation that determines which Hilt component(s) to install the module into.
- @Qualifire - A qualifier is an annotation that you use to identify a specific binding for a type when that type has multiple bindings defined.
- @Retention - 

## Generated components for android classes
### Hilt Components               Injected For
- Application Component           Application
- ActivityRetainedComponent       ViewModel
- ActivityComponent               Activity
- Fragment                        Fragment
- ViewComponent                   View
- ViewWithFragmentComponent       View annoted with @WithViewFragmentBinding
- ServiceComponent                Service

- Hilt does not generate component for Broadcast Receiver directly from application component
- Hilt Automatically create and destroy instaces of generated component classes

## Component Scope 
#### Android Class -- Generated Component -- Scope
- Application -- ApplicationComponent -- @Signleton
- ViewModel -- ActivityRetainedComponent -- @ActivityRetainedScope
- Activity -- ActivityComponent -- @ActivityScoped
- Fragment -- FragmentComponent -- @FragmentScoped
- View -- ViewComponent -- @ViewScoped
- View annoted with @WithFragmentBiding -- ViewWithFragmentComponent -- ViewScoped
- Service -- ServiceComponent -- ServiceScoped

- Scoping a binding a component can costly because the provided object stays in memory untill that component is destroyed.
- application scope hierarcy shoud be in a scope Hietarcy
- by default binding in Hilt are unscoped.




