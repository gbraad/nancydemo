NancyFX on .NET Core demo application
=====================================


## Install

### Windows

Install [.NET Core 2](https://www.microsoft.com/net/core/)
```
PS> dotnet restore
```

### CentOS 7
```
$ yum install centos-release-dotnet
$ yum install rh-dotnet20
$ scl enable rh-dotnet20 bash
$ dotnet restore
```

## Running


### Development (Windows/Linux)

```
$ dotnet run
```

    Hosting environment: Production
    Content root path: /workspace/src/github.com/gbraad/nancydemo
    Now listening on: http://localhost:5000
    Application started. Press Ctrl+C to shut down.

### OpenShift (Minishift)

You need the .NET Core runtime and S2i builder images. These are available after importing the following imagestream defintions:

```
$ oc create --namespace openshift -f https://raw.githubusercontent.com/redhat-developer/s2i-dotnetcore/master/dotnet_imagestreams.json
```

On Minishift this is possible after applying the [dotnet add-on](https://github.com/minishift/minishift-addons/tree/master/add-ons/dotnet)
```
$ minishift addons apply dotnet
```

After this is done, you can easily deploy this application:
```
$ oc new-app --name=nancydemo dotnet:2.0~https://github.com/gbraad/nancydemo
```
