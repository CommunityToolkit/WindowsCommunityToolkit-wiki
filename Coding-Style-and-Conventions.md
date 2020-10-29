In general, the project follows the [C# Coding Convention](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions) and [Framework Design Guidelines](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/). We use tools like StyleCop to help enforce some of the rules mentioned below. 

* DO NOT require that users perform any extensive initialization before they can start programming basic scenarios.
* DO provide good defaults for all values associated with parameters, options, etc.
* DO ensure that APIs are intuitive and can be successfully used in basic scenarios without referring to the reference documentation (though see below).
* DO communicate incorrect usage of APIs as soon as possible.
* DO design an API by writing code samples for the main scenarios. Only then, you define the object model that supports those code samples.
* DO NOT use regions. DO use partial classes instead.
* DO declare static dependency properties at the top of their file.
* DO NOT seal controls.
* DO use extension methods over static methods where possible.
* DO NOT return true or false to give success status. Throw exceptions if there was a failure.
* DO use verbs like GET.
* DO NOT use verbs that are not already used like fetch.

### Documentation

* DO NOT expect that your API is so well designed that it needs no documentation. No API is that intuitive.
* DO provide great documentation with all APIs.
* DO use readable and self-documenting identifier names.
* DO use consistent naming and terminology.
* DO provide strongly typed APIs.
* DO use verbose identifier names.

### Files and Folders 

* DO NOT create a new namespace for every folder.
* DO associate no more than one class per file.
* DO use folders to group classes based on features.
