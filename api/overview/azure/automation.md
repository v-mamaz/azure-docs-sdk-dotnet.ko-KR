---
title: ".NET용 Azure Automation 라이브러리"
description: ".NET용 Azure Automation 라이브러리에 대한 참조"
keywords: Azure, .NET, SDK, API, Automation
author: camsoper
ms.author: casoper
manager: douge
ms.date: 07/21/2017
ms.topic: reference
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.openlocfilehash: 1e1b5a662947503ff71f3e4a9b67f20a1e2d5f87
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-automation-libraries-for-net"></a>.NET용 Azure Automation 라이브러리

## <a name="overview"></a>개요

Microsoft Azure Automation은 사용자가 클라우드 및 엔터프라이즈 환경에서 일반적으로 수행되는 작업을 자동화하는 방법을 제공합니다. 

자세한 내용은 [Azure Automation 개요](/azure/automation/automation-intro)를 참조하세요.

## <a name="management-library"></a>관리 라이브러리

관리 라이브러리를 사용하여 Runbook 및 작업을 관리하고 필요한 상태 구성 설정을 관리합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Automation)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.Automation
```

```bash
dotnet add package Microsoft.Azure.Management.Automation
```

### <a name="code-example"></a>코드 예제

다음 예제에서는 기존 Runbook에 따라 새 작업을 시작하는 방법을 보여 줍니다.

```csharp
/*
  using Microsoft.Azure.Management.Automation;
*/
AutomationManagementClient client =
    new AutomationManagementClient(new CertificateCloudCredentials(subscriptionId, cert));

// Create job create parameters
JobCreateParameters jcParam = new JobCreateParameters
{
    Properties = new JobCreateProperties
    {
        Runbook = new RunbookAssociationProperty
        {
            Name = runbookName
        },
        Parameters = null // optional parameters here
    }
};

// create runbook job. This gives back the Job
Job job = automationManagementClient.Jobs.Create(automationAccountName, jcParam).Job;
```

> [!div class="nextstepaction"]
> [관리 API 탐색](/dotnet/api/overview/azure/automation/management)

## <a name="samples"></a>샘플

* [AzureBot](https://github.com/Microsoft/AzureBot)은 [Bot Framework](https://docs.microsoft.com/bot-framework/) 및 [Cognitive Services](/cognitive-services)가 포함된 자동화 라이브러리를 사용하여 Azure에서 개발자의 생산성을 향상시켜 줍니다.

앱에서 사용할 수 있는 [.NET 샘플 코드](https://azure.microsoft.com/resources/samples/?platform=dotnet)를 추가로 탐색합니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package