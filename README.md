# TacitusLogger.Contributors.MachineInfo

> Extension contributor for TacitusLogger that generates additional info related to the machine on which the log was produced.
 
Dependencies:  
* .Net Standard >= 2.0  
* TacitusLogger >= 0.1.3 
  
> Attention: `TacitusLogger.Contributors.MachineInfo` is currently in **Alpha phase**. This means you should not use it in any production code.

## Installation

The NuGet <a href="https://www.nuget.org/packages/TacitusLogger.Contributors.MachineInfo" target="_blank">package</a>:

```powershell
PM> Install-Package TacitusLogger.Contributors.MachineInfo
```

## Examples

### Adding machine info contributor to the logger
With builders:
```cs
Logger logger = LoggerBuilder.Logger()
                             .Contributors()
                                 .MachineInfo()
                             .BuildContributors()
                             .ForAllLogs()
                                 .Console().Add()
                             .BuildLogger();
```
Directly:
```cs
MachineInfoContributor machineInfo = new MachineInfoContributor(); 

Logger logger = new Logger();
logger.AddLogContributor(machineInfo); 
```
### Explicitly specifying name and status of machine info contributor
With builders:
```cs
Logger logger = LoggerBuilder.Logger()
                             .Contributors()
                                 .MachineInfo(true, "Source machine")
                             .BuildContributors()
                             .ForAllLogs()
                                 .Console().Add()
                             .BuildLogger();
```
Directly:
```cs
MachineInfoContributor machineInfo = new MachineInfoContributor("Source machine");
machineInfo.SetActive(true);

Logger logger = new Logger();
logger.AddLogContributor(machineInfo);
``` 
### Explicitly specifying mutable status of machine info contributor
With builders:
```cs
MutableSetting<bool> status = Setting<bool>.From.Variable(true);

Logger logger = LoggerBuilder.Logger()
                             .Contributors()
                                 .MachineInfo(status)
                             .BuildContributors()
                             .ForAllLogs()
                                 .Console().Add()
                             .BuildLogger();
```
Directly:
```cs
MutableSetting<bool> status = Setting<bool>.From.Variable(true); 
MachineInfoContributor machineInfo = new MachineInfoContributor("Source machine");
machineInfo.SetActive(status);

Logger logger = new Logger();
logger.AddLogContributor(machineInfo); 
``` 

## License

[APACHE LICENSE 2.0](https://www.apache.org/licenses/LICENSE-2.0)

## See also

TacitusLogger:  

- [TacitusLogger](https://github.com/khanlarmammadov/TacitusLogger) - A simple yet powerful .NET logging library.

Destinations:

- [TacitusLogger.Destinations.MongoDb](https://github.com/khanlarmammadov/TacitusLogger.Destinations.MongoDb) - Extension destination for TacitusLogger that sends logs to MongoDb database.
- [TacitusLogger.Destinations.RabbitMq](https://github.com/khanlarmammadov/TacitusLogger.Destinations.RabbitMq) - Extension destination for TacitusLogger that sends logs to the RabbitMQ exchanges.
- [TacitusLogger.Destinations.Email](https://github.com/khanlarmammadov/TacitusLogger.Destinations.Email) - Extension destination for TacitusLogger that sends logs as emails using SMTP protocol.
- [TacitusLogger.Destinations.EntityFramework](https://github.com/khanlarmammadov/TacitusLogger.Destinations.EntityFramework) - Extension destination for TacitusLogger that sends logs to database using Entity Framework ORM.
- [TacitusLogger.Destinations.Trace](https://github.com/khanlarmammadov/TacitusLogger.Destinations.Trace) - Extension destination for TacitusLogger that sends logs to System.Diagnostics.Trace listeners.  
  
Dependency injection:
- [TacitusLogger.DI.Ninject](https://github.com/khanlarmammadov/TacitusLogger.DI.Ninject) - Extension for Ninject dependency injection container that helps to configure and add TacitusLogger as a singleton.
- [TacitusLogger.DI.Autofac](https://github.com/khanlarmammadov/TacitusLogger.DI.Autofac) - Extension for Autofac dependency injection container that helps to configure and add TacitusLogger as a singleton.
- [TacitusLogger.DI.MicrosoftDI](https://github.com/khanlarmammadov/TacitusLogger.DI.MicrosoftDI) - Extension for Microsoft dependency injection container that helps to configure and add TacitusLogger as a singleton.  

Log contributors:

- [TacitusLogger.Contributors.ThreadInfo](https://github.com/khanlarmammadov/TacitusLogger.Contributors.ThreadInfo) - Extension contributor for TacitusLogger that generates additional info related to the thread on which the logger method was called.