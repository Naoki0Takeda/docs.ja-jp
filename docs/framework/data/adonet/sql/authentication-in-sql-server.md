---
title: SQL Server での認証
ms.date: 05/22/2018
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.openlocfilehash: 09f7825fd6b4f852b24142ea297c078bd8a1e221
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040270"
---
# <a name="authentication-in-sql-server"></a>SQL Server での認証
SQL Server は、Windows 認証モードと混合モードの 2 つの認証モードをサポートしています。  
  
- Windows 認証は既定の認証モードです。この SQL Server セキュリティ モデルは、Windows と緊密に統合されていることから統合セキュリティと呼ばれることもあります。 特定の Windows ユーザーおよび Windows グループが、信頼されたアカウントとして SQL Server へのログインが許可されます。 既に認証済みの Windows ユーザーは別途資格情報を提示する必要はありません。  
  
- 混合モードは、Windows による認証と SQL Server による認証の両方がサポートされます。 SQL Server 内でユーザー名とパスワードのペアが管理されます。  
  
> [!IMPORTANT]
> できるだけ Windows 認証を使用することをお勧めします。 Windows 認証では、暗号化された一連のメッセージを使用して SQL Server のユーザーを認証します。 SQL Server ログインが使用されると、SQL Server のログイン名と暗号化されたパスワードがネットワーク経由で渡されるため、セキュリティが低下します。  
  
 Windows 認証では、既に Windows にログオンしているユーザーが別途 SQL Server にログオンする必要はありません。 次の `SqlConnection.ConnectionString` では、ユーザーにユーザー名またはパスワードの入力を要求することなく Windows 認証を指定します。  
  
```csharp  
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;"
```  
  
> [!NOTE]
> ログインは、データベース ユーザーとは異なります。 ログインまたは Windows グループは、別個の操作でデータベース ユーザーまたはロールにマップする必要があります。 その後、ユーザーまたはロールに対してデータベース オブジェクトにアクセスするための権限を付与することになります。  
  
## <a name="authentication-scenarios"></a>認証のシナリオ  
 通常、以下の状況では Windows 認証が最良の選択肢です。  
  
- ドメイン コントローラーが存在する。  
  
- アプリケーションとデータベースが同じコンピューター上に存在する。  
  
- SQL Server Express または LocalDB のインスタンスを使用しています。  
  
 次の状況では、SQL Server ログインを使用することがよくあります。  
  
- ワークグループが存在する。  
  
- ユーザーが別の信頼されていないドメインから接続する。  
  
- ASP.NET などのインターネットアプリケーション。  
  
> [!NOTE]
> Windows 認証を指定しても、SQL Server ログインは無効になりません。 高い権限を持つ SQL Server ログインを無効にするには、Transact-SQL ステートメント ALTER LOGIN DISABLE を使用します。  
  
## <a name="login-types"></a>ログインの種類  
 SQL Server では、次の3種類のログインがサポートされています。  
  
- ローカル Windows ユーザー アカウントまたは信頼されたドメイン アカウント。 SQL Server が Windows に依存する形で Windows ユーザー アカウントを認証します。  
  
- Windows グループ。 Windows グループへのアクセス権を付与すると、そのグループに属しているすべての Windows ユーザー ログインにアクセス権が付与されます。  
  
- SQL Server ログイン。 SQL Server はユーザー名およびパスワードのハッシュを master データベースに格納し、内部の認証方法を使ってログイン試行を検証します。  
  
> [!NOTE]
> SQL Server には、コード署名にのみ使用される証明書または非対称キーから作成されたログインが用意されています。 SQL Server への接続には使用できません。  
  
## <a name="mixed-mode-authentication"></a>混合モード認証  
 混合モード認証を使用する場合は、SQL Server に格納される SQL Server ログインを作成する必要があります。 さらに、SQL Server のユーザー名とパスワードを実行時に指定する必要があります。  
  
> [!IMPORTANT]
> SQL Server をインストールすると、`sa` ("system administrator" の略) という名前の SQL Server ログインが作成されます。 `sa` ログインには強力なパスワードを割り当て、アプリケーションで `sa` ログインを使用することは避けてください。 `sa` ログインは、サーバー全体に対する取り消し不可能な管理者の資格情報を持つ `sysadmin` 固定サーバー ロールにマップされます。 システム管理者のアクセス権が攻撃者によって取得された場合の潜在的な損害は計り知れません。 既定では、Windows `BUILTIN\Administrators` グループ (ローカル管理者のグループ) のすべてのメンバーが `sysadmin` ロールに所属しますが、sysadmin ロールから Windows の Administrators グループのメンバーを削除することもできます。  
  
 SQL Server には、[!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] 以降のバージョンで実行されている場合に SQL Server ログインに Windows パスワードポリシーメカニズムが用意されています。 パスワードの複雑性のポリシーは、考えられるパスワードの数を増やすことにより、総当たり攻撃を防ぐようにデザインされています。 SQL Server は、[!INCLUDE[winxpsvr](../../../../../includes/winxpsvr-md.md)] で使用されるのと同じ複雑さと有効期限ポリシーを SQL Server 内で使用されるパスワードに適用できます。  
  
> [!IMPORTANT]
> ユーザー入力から文字列を連結することによって接続文字列を構築している場合、接続文字列のインジェクション攻撃に対して脆弱になります。 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> を使用すると、構文的に正しい接続文字列を実行時に作成できます。 詳細については、「[接続文字列ビルダー](../connection-string-builders.md)」をご覧ください。  
  
## <a name="external-resources"></a>外部リソース  
 詳細については、次のリソースを参照してください。  
  
|リソース|説明|  
|--------------|-----------------|  
|[プリンシパル](/sql/relational-databases/security/authentication-access/principals-database-engine)|SQL Server のログインとその他のセキュリティプリンシパルについて説明します。|  
  
## <a name="see-also"></a>関連項目

- [ADO.NET アプリケーションのセキュリティ保護](../securing-ado-net-applications.md)
- [SQL Server におけるアプリケーション セキュリティのシナリオ](application-security-scenarios-in-sql-server.md)
- [データ ソースへの接続](../connecting-to-a-data-source.md)
- [接続文字列](../connection-strings.md)
- [ADO.NET の概要](../ado-net-overview.md)
