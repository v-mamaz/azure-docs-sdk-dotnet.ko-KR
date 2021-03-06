---
title: .NET용 Azure Cosmos DB 라이브러리
description: .NET용 Azure Cosmos DB 라이브러리에 대한 참조
ms.date: 08/31/2018
ms.topic: reference
ms.service: cosmos-db
ms.openlocfilehash: 8ff565f1cd72eec2f574b45d04ceac526b8c5eb0
ms.sourcegitcommit: 01ec3adba39a6f946015552c28da0a9a6bb57180
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112021"
---
# <a name="azure-cosmos-db-libraries-for-net"></a>.NET용 Azure Cosmos DB 라이브러리

## <a name="overview"></a>개요

[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction)는 전 세계에 배포된 다중 모델 데이터베이스 서비스입니다. 해당 서비스는 포괄적인 SLA를 제공하는 원하는 수의 지역에서 처리량 및 저장소 크기를 탄력적 및 독립적으로 조정할 수 있도록 설계되었습니다. Azure Cosmos DB를 사용하면 API 및 프로그래밍 모델을 사용하여 문서, 키-값, 넓은 열 및 그래프 데이터베이스를 저장하고 액세스할 수 있습니다. 

[Cosmos DB 시작](https://docs.microsoft.com/azure/cosmos-db/create-sql-api-dotnet).

## <a name="client-library"></a>클라이언트 라이브러리

Azure Cosmos DB .NET 클라이언트 라이브러리를 사용하여 기존 Azure Cosmos DB 데이터 저장소에 액세스하고 데이터를 저장합니다. 새 Azure Cosmos DB 계정 만들기를 자동화하려면 Azure Portal, CLI 또는 PowerShell을 사용합니다.

Visual Studio [패키지 관리자 콘솔][PackageManager] 또는 [.NET Core CLI][DotNetCLI]를 사용하여 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core)를 직접 설치합니다.

2.x 버전을 설치하려면:

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.DocumentDB.Core
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.DocumentDB.Core
```

.NET 표준을 대상으로 버전 3.0의 미리 보기를 설치하려면: 

#### <a name="visual-studio-package-manager"></a>Visual Studio 패키지 관리자

```powershell
Install-Package Microsoft.Azure.Cosmos -prerelease
```

#### <a name="net-core-cli"></a>.NET Core CLI

```bash
dotnet add package Microsoft.Azure.Cosmos
```


### <a name="code-example"></a>코드 예제

이 예제에서는 기존 Azure Cosmos DB SQL API 데이터베이스에 연결하고 컬렉션에서 문서를 읽고 `Item` 개체로 deserialize합니다. 이 예제에서는 .NET SDK의 2.x 버전을 사용합니다.   

```csharp
/* Include this "using" directive...
using Microsoft.Azure.Documents.Client;
*/

DocumentClient client = new DocumentClient(endpointUri, authKeyString);
Uri documentUri = UriFactory.CreateDocumentUri("MyDatabaseName", "MyCollectionName", "DocumentId");
SomeClass myObject = client.ReadDocumentAsync<SomeClass>(documentUri).ToString();
```

이 예제는 기존 Azure Cosmos DB SQL API 데이터베이스에 연결하고, 새 데이터베이스와 컨테이너를 만들고, 컨테이너에서 항목을 읽고, `TodoItem` 객체로 deserialize합니다. 이 예제에서는 .NET SDK의 3.x 버전을 사용합니다.   

```csharp
using (CosmosClient cosmosClient = new CosmosClient("endpoint", "primaryKey"))
{
    // Read item from container
    CosmosItemResponse<TodoItem> todoItemResponse = await cosmosClient.Databases["DatabaseId"].Containers["ContainerId"].Items.ReadItemAsync<TodoItem>("partitionKeyValue", "ItemId");
}
```

> [!div class="nextstepaction"]
> [클라이언트 API 탐색](/dotnet/api/overview/azure/cosmosdb/client)

## <a name="samples"></a>샘플

* [Azure Cosmos DB의 SQL API (버전 2.x)를 사용하여 .NET 앱 개발](https://github.com/Azure-Samples/documentdb-dotnet-todo-app/)
* [Azure Cosmos DB의 SQL API (버전 3.x 미리보기)를 사용하여 .NET 앱 개발](https://github.com/Azure-Samples/cosmos-dotnet-todo-app/)
* [Azure Cosmos DB의 SQL API (버전 3.x 미리보기)를 사용하여 .NET Core 앱 개발](https://github.com/Azure-Samples/cosmos-dotnet-core-getting-started)

Azure Cosmos DB 샘플의 [전체 목록](https://azure.microsoft.com/resources/samples/?platform=dotnet&term=cosmosdb)을 봅니다.

[PackageManager]: https://docs.microsoft.com/nuget/tools/package-manager-console
[DotNetCLI]: https://docs.microsoft.com/dotnet/core/tools/dotnet-add-package
