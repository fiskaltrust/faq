## Question
Can I run the fiskaltrust Middleware on Linux?

## Question
What are the requirements and limitations of the Middleware when running on Linux?

## Metadata tags
lang-en, market-de, middleware

## Answer
Starting with version 1.3.3, it's possible to run the German Middleware on Linux, using [Mono](https://www.mono-project.com/). Just configure a Cashbox and download the Linux launcher via the respective button in the Cashbox overview. Like on Windows, the downloaded zip file contains scripts to install and test the Middleware.

### Requirements
In general, it's possible to run the Middleware on each Linux distribution that is supported by Mono (_Ubuntu_, _Debian_, _Raspbian_, _CentOS_ and _Fedora_, including their derivatives). Most testing at fiskaltrust is performed with Ubuntu and Debian, and we hence recommend to use these distributions.

**Please make sure to install the latest Mono version**. The default versions in the package repositories are usually extremely outdated, so please follow the official [Mono guidelines](https://www.mono-project.com/download/stable/#download-lin-ubuntu) to get the latest packages. We recommend to use at least version 6.8.0, if possible.

Other than that, no specific software needs to be installed (aside from the dependencies Mono has).

### Supported packages
- Both Entity Framework and SQLite queues can be launched on Linux, starting from version 1.3.3. 
- Currently, SCU support is limited to the fiskaly and the Cryptovision packages, starting from version 1.3.3. Other SCUs (like Swissbit) will be supported soon.

### Limitations
Currently, the Middleware only supports gRPC and REST when executed on Linux. This means that SOAP is right now not supported (due to open bugs in Mono's WCF implementation). 

If you haven't already decided for a communication technology, we strongly recommend gRPC, especially in Linux scenarios, as it provides a cleaner, more stable interface. Please refer to our demo project (currently available in [C#](https://github.com/fiskaltrust/middleware-demo-dotnet), [Java](https://github.com/fiskaltrust/middleware-demo-java), [Node.js](https://github.com/fiskaltrust/middleware-demo-node) and [others](https://github.com/fiskaltrust)) for sample implementations.

#### REST limitations
When using REST, the HTTP endpoint slightly differs from the Windows version, as the version prefix cannot be included because of the mentioned Mono issues. Hence, a REST URL on Linux would look like this: `http://localhost:1500/a4c4e466-721a-4011-a9a5-a23827a21b45/sign` (instead of `../v1/sign`).

In addition, if REST is used, a gRPC endpoint needs to be configured as the **primary** endpoint of the Queue and the SCU, so it can be properly used by our packages.

We will unify the experiences on Linux and Windows in an upcoming version.

