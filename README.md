# Tutorial
RESTar is a powerful REST API Framework for Starcounter applications, that is free to use and easy to set up in new or existing applications. Using RESTar in your Starcounter projects will give your applications all sorts of REST super powers, with minimal effort. This tutorial will give a basic introduction to RESTar, and how to use it in a simple Starcounter application. For more information, please se the complete [RESTar Specification](https://goo.gl/TIkN7m), which outlines all the features of RESTar.

## Getting started
To get started, install RESTar from NuGet, either by browsing for `RESTar` in the **NuGet Package Manager** or by running the following command in the **Package Manager Console**:

```Install-Package RESTar```

All we need to do then, to enable RESTar in a given application, is to make a call to `RESTar.RESTarConfig.Init()` somewhere in the application code where it's called once every time the app starts. `Init()` will register the necessary handlers, collect all resources and make them available over a REST API. Here is a simple RESTar application.

```c#
public class Program
{
    public static void Main()
    {
        RESTarConfig.Init(port: 8282, uri: "/myservice");
        // The 'port' argument decides which HTTP port to register the REST handlers on
        // The 'uri' argument sets the root uri of the REST API
    }
}
```
The application above is not very useful, however, since it doesn't expose any resources except the resources that come with RESTar. Let's change that. To register a Starcounter database class with RESTar, so that RESTar can expose it for operations over the REST API, we simply 
