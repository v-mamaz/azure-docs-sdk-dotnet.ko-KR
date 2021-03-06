---
title: .NET용 Azure 계산 라이브러리
description: .NET용 Azure 계산 라이브러리에 대한 참조
ms.date: 10/19/2017
ms.topic: reference
ms.service: virtual-machines
ms.openlocfilehash: ee481e0f2448a874629bec36a719e7682407d320
ms.sourcegitcommit: 5d9b713653b3d03e1d0a67f6e126ee399d1c2a60
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47190696"
---
# <a name="azure-virtual-machine-libraries-for-net"></a>.NET용 Azure 가상 머신 라이브러리

## <a name="overview"></a>개요

Linux 또는 Windows를 실행하는 요청 시 확장 가능한 컴퓨팅 리소스입니다.

Azure 가상 머신을 시작하려면 [Azure Portal을 사용하여 Linux 가상 머신 만들기](https://review.docs.microsoft.com/azure/virtual-machines/linux/quick-create-portal)를 참조하세요.

## <a name="management-apis"></a>관리 API

관리 API를 사용하여 코드에서 Azure의 Windows 및 Linux 가상 머신을 생성, 구성 및 확장할 수 있습니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.Management.Compute.Fluent)를 직접 설치합니다.

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Management.Compute.Fluent
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.Management.Compute.Fluent
```

### <a name="code-example"></a>코드 예제

Windows VM을 만듭니다.

```csharp
/* Include these "using" directives...
using Microsoft.Azure.Management.Compute.Fluent;
using Microsoft.Azure.Management.Compute.Fluent.Models;
using Microsoft.Azure.Management.ResourceManager.Fluent.Core;
*/

IVirtualMachine windowsVM = azure.VirtualMachines.Define("MyVirtualMachine")
    .WithRegion(Region.USEast)
    .WithNewResourceGroup("MyResourceGroup")
    .WithNewPrimaryNetwork("10.0.0.0/28")
    .WithPrimaryPrivateIPAddressDynamic()
    .WithNewPrimaryPublicIPAddress("MyIPAddressLabel")
    .WithPopularWindowsImage(KnownWindowsVirtualMachineImage.WindowsServer2012R2Datacenter)
    .WithAdminUsername("UserName")
    .WithAdminPassword("Password")
    .WithSize(VirtualMachineSizeTypes.StandardD3V2)
    .Create();
```

> [!div class="nextstepaction"]
> [관리 API 탐색](https://docs.microsoft.com/dotnet/api/overview/azure/virtualmachines/management?view=azure-dotnet)

### <a name="samples"></a>샘플

* [가상 머신 만들기 및 관리](/dotnet/azure/dotnet-sdk-azure-virtual-machine-samples)
* [.NET에서 템플릿을 사용하여 SSH 사용 VM 배포(영문)](https://azure.microsoft.com/resources/samples/resource-manager-dotnet-template-deployment/)

가상 머신 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=VM)을 봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
