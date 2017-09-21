---
title: ".NET용 Azure 관리 라이브러리 샘플 지침"
description: ".NET용 Azure 관리 라이브러리를 사용하여 리소스를 만들고 업데이트하는 샘플 코드를 가져옵니다."
keywords: "Azure, .NET, SDK, API, 샘플, 예제"
author: camsoper
ms.author: casoper
manager: douge
ms.date: 06/20/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: dotnet
ms.service: multiple
ms.assetid: 
ms.openlocfilehash: ffda7cca724962e6f953432c5cab04485ddabb03
ms.sourcegitcommit: d95a6ad3774a49b16f652e40e7860e47636c7ad0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="azure-management-libraries-for-net-sample-instructions"></a>.NET용 Azure 관리 라이브러리 샘플 지침

이 문서에서는 .NET용 Azure 관리 라이브러리 샘플을 실행하는 데 필요한 필수 구성 요소 및 인증에 대해 설명합니다.

## <a name="prerequisties"></a>필수 구성 요소 

* [Visual Studio 2017](https://www.visualstudio.com/vs/) 또는 [.NET Core SDK](https://www.microsoft.com/net/download/core)
* [Microsoft Azure 구독](https://azure.microsoft.com/free/)
* [Git 명령줄 클라이언트](https://git-scm.com/)
* [Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps)

## <a name="authentication-for-all-samples"></a>모든 샘플에 대한 인증

[!include[Create service principal](includes/create-sp.md)]

[!include[File-based authentication](includes/file-based-auth.md)]

## <a name="running-the-samples"></a>샘플 실행

Git를 사용하여 샘플을 복제한 후에는 Visual Studio에서 샘플을 열고 IDE를 사용하여 샘플을 실행할 수 있습니다.  또는 .NET Core SDK를 사용하고 다음과 같이 명령줄에서 샘플을 빌드하고 실행합니다.

```cmd
git clone https://github.com/Azure-Samples/app-service-dotnet-configure-deployment-sources-for-web-apps.git
cd app-service-dotnet-configure-deployment-sources-for-web-apps
dotnet restore
dotnet run
```