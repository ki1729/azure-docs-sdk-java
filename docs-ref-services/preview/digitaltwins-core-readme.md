---
title: Azure IoT Digital Twins client library for Java
keywords: Azure, java, SDK, API, azure-digitaltwins-core, digitaltwins
author: maggiepint
ms.author: magpint
ms.date: 10/01/2020
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: java
ms.service: digitaltwins
---

# Azure IoT Digital Twins client library for Java - Version 1.0.0-beta.3 


This library provides access to the Azure Digital Twins service for managing twins, models, relationships, etc.

  [Source code][source] | [Package](https://search.maven.org/artifact/com.azure/azure-digitaltwins-core)

## Getting started

The complete Microsoft Azure SDK can be downloaded from the [Microsoft Azure downloads][microsoft_sdk_download] page, and it ships with support for building deployment packages, integrating with tooling, rich command line tooling, and more.

For the best development experience, developers should use the official Microsoft Maven packages for libraries. Maven packages are regularly updated with new functionality and hotfixes.

### Include the Package

[//]: # ({x-version-update-start;com.azure:azure-digitaltwins-core;current})

```xml
<dependency>
  <groupId>com.azure</groupId>
  <artifactId>azure-digitaltwins-core</artifactId>
  <version>1.0.0-beta.3</version>
</dependency>
```

[//]: # ({x-version-update-end})

### Prerequisites

- A Microsoft Azure Subscription
  - To call Microsoft Azure services, create an [Azure subscription][azure_sub].
- An Azure Digital Twins instance
  - In order to use the Azure Digital Twins SDK, first create a Digital Twins instance using one of options:
    - Using [Azure portal][azure_portal]
    - Using [Azure Management APIs][azure_rest_api]
    - Using [Azure CLI][azure_cli]
      - You will need to install azure cli and the [Azure IoT extension][iot_cli_extension] for Azure CLI.
      - Refer to [IoT CLI documentation][iot_cli_doc] for more information on how to create and interact with your Digital Twins instance.

### Authenticate the Client

In order to interact with the Azure Digital Twins service, you will need to create an instance of a [TokenCredential class][token_credential] and pass it to the constructor of your [DigitalTwinsClientBuilder](https://github.com/Azure/azure-sdk-for-java/blob/azure-digitaltwins-core_1.0.0-beta.3/sdk/digitaltwins/azure-digitaltwins-core/src/main/java/com/azure/digitaltwins/core/DigitalTwinsClientBuilder.java).

## Key concepts

Azure Digital Twins Preview is an Azure IoT service that creates comprehensive models of the physical environment.
It can create spatial intelligence graphs to model the relationships and interactions between people, spaces, and devices.

You can learn more about Azure Digital Twins by visiting [Azure Digital Twins Documentation][digital_twins_documentation]

## Examples

You can familiarize yourself with different APIs using [samples for Digital Twins](https://github.com/Azure/azure-sdk-for-java/tree/azure-digitaltwins-core_1.0.0-beta.3/sdk/digitaltwins/azure-digitaltwins-core/src/samples).

## Source code folder structure

### /src/main/java/com/azure/digitaltwins/core

- The Digital Twins client builder [`DigitalTwinsClientBuilder`](https://github.com/Azure/azure-sdk-for-java/blob/azure-digitaltwins-core_1.0.0-beta.3/sdk/digitaltwins/azure-digitaltwins-core/src/main/java/com/azure/digitaltwins/core/DigitalTwinsClientBuilder.java)
- The Digital Twins public sync and async clients [`DigitalTwinsClient`](https://github.com/Azure/azure-sdk-for-java/blob/azure-digitaltwins-core_1.0.0-beta.3/sdk/digitaltwins/azure-digitaltwins-core/src/main/java/com/azure/digitaltwins/core/DigitalTwinsClient.java), [`DigitalTwinsAsyncClient`](https://github.com/Azure/azure-sdk-for-java/blob/azure-digitaltwins-core_1.0.0-beta.3/sdk/digitaltwins/azure-digitaltwins-core/src/main/java/com/azure/digitaltwins/core/DigitalTwinsAsyncClient.java)
- [`models` package](https://github.com/Azure/azure-sdk-for-java/tree/azure-digitaltwins-core_1.0.0-beta.3/sdk/digitaltwins/azure-digitaltwins-core/src/main/java/com/azure/digitaltwins/core/models)

### /src/swagger

A local copy of the swagger file that defines the structure of the REST APIs supported by the Azure Digital Twins service.

To regenerate the code, run the powershell script [generate.ps1](https://github.com/Azure/azure-sdk-for-java/blob/azure-digitaltwins-core_1.0.0-beta.3/sdk/digitaltwins/azure-digitaltwins-core/generate.ps1).

## Troubleshooting

All service operations will throw ErrorResponseException on failure reported by the service, with helpful error codes and other information.

For example, use the `getModel` operation to check if the model exists before creating it.

```java
try {
    syncClient.getModel("someRandomModelId");
}
catch (ErrorResponseException ex) {
    if (ex.getResponse().getStatusCode() == HttpURLConnection.HTTP_NOT_FOUND) {
        return id;
    } else {
        // This request should not retried if it encounters a 401 error, for instance
        throw new IllegalStateException("Encountered unexpected error while searching for unique id", ex);
    }
}
```

## Next steps

See implementation examples with our [code samples](https://github.com/Azure/azure-sdk-for-java/tree/azure-digitaltwins-core_1.0.0-beta.3/sdk/digitaltwins/azure-digitaltwins-core/src/samples).

## Contributing

This project welcomes contributions and suggestions.
Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us the rights to use your contribution.
For details, visit <https://cla.microsoft.com.>

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide a CLA and decorate the PR appropriately (e.g., label, comment).
Simply follow the instructions provided by the bot.
You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct][code_of_conduct].
For more information see the Code of Conduct FAQ or contact opencode@microsoft.com with any additional questions or comments.

<!-- LINKS -->
[microsoft_sdk_download]: https://azure.microsoft.com/downloads/?sdk=java
[azure_cli]: https://docs.microsoft.com/cli/azure
[azure_sub]: https://azure.microsoft.com/free/
[source]: https://github.com/Azure/azure-sdk-for-java/tree/azure-digitaltwins-core_1.0.0-beta.3/sdk/digitaltwins/azure-digitaltwins-core
[code_of_conduct]: https://opensource.microsoft.com/codeofconduct/
[nuget]: https://www.nuget.org/
[azure_portal]: https://portal.azure.com/
[azure_rest_api]: https://docs.microsoft.com/rest/api/azure/
[azure_core_library]: https://github.com/Azure/azure-sdk-for-java/tree/azure-digitaltwins-core_1.0.0-beta.3/sdk/core/azure-core
[token_credential]: https://docs.microsoft.com/java/api/com.azure.core.credential.tokencredential?view=azure-java-stable
[digital_twins_documentation]: https://docs.microsoft.com/azure/digital-twins/
[azure_cli]: https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest
[iot_cli_extension]: https://docs.microsoft.com/azure/iot-pnp/howto-use-iot-pnp-cli
[iot_cli_doc]: https://docs.microsoft.com/cli/azure/ext/azure-iot/dt?view=azure-cli-latest

