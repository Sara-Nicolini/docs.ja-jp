---
title: "基本認証でのトランスポート セキュリティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
caps.latest.revision: 18
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 18
---
# 基本認証でのトランスポート セキュリティ
次の図は、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のサービスとクライアントを示しています。  サーバーには、SSL \(Secure Sockets Layer\) に使用できる有効な X509 証明書が必要であり、クライアントはサーバーの証明書を信頼する必要があります。  さらに、Web サービスには使用可能な SSL が既に実装されています。  インターネット インフォメーション サービス \(IIS\) で基本認証を有効にする方法についての[!INCLUDE[crabout](../../../../includes/crabout-md.md)] 「[http:\/\/go.microsoft.com\/fwlink\/?LinkId\=83822](http://go.microsoft.com/fwlink/?LinkId=83822)」を参照してください。  
  
 ![基本認証を使用する場合のトランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")  
  
|特徴|説明|  
|--------|--------|  
|セキュリティ モード|Transport|  
|相互運用性|既存の Web サービス クライアントとサービスを使用する|  
|認証 \(サーバー\)<br /><br /> 認証 \(クライアント\)|○ \(HTTPS を使用\)<br /><br /> ○ \(ユーザー名とパスワードを使用\)|  
|整合性|はい|  
|機密性|はい|  
|Transport|HTTPS|  
|バインディング|<xref:System.ServiceModel.WSHttpBinding>|  
  
## サービス  
 次のコードと構成は、別々に実行します。  次のいずれかの操作を行います。  
  
-   構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。  
  
-   提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。  
  
### コード  
 次のコードでは、転送セキュリティ用の Windows ドメイン ユーザー名とパスワードを使用するサービス エンドポイントを作成する方法を示します。  サービスには、クライアントに対する認証を行うための X 509 証明書が必要になります。  詳細については、「[証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)」および「[方法 : SSL 証明書を使用してポートを構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)」を参照してください。  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## 構成  
 次の例では、トランスポート レベルのセキュリティの基本認証を使用するサービスを構成します。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"   
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"   
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## Client  
  
### コード  
 次のコードは、ユーザー名とパスワードが含まれるクライアント コードを示しています。  ユーザーは、有効な Windows ユーザー名とパスワードを指定する必要があります。  ユーザー名とパスワードを返すコードは、ここに示されていません。  ダイアログボックスまたは他のインターフェースを使用して、ユーザーにこれらの情報を照会してください。  
  
> [!NOTE]
>  ユーザー名とパスワードは、コードを使ってのみ設定できます。  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### 構成  
 次のコードは、クライアントの構成を示しています。  
  
> [!NOTE]
>  構成を使用してユーザー名とパスワードを設定することはできません。  ここに示した構成には、ユーザー名とパスワードを設定するためのコードを補う必要があります。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## 参照  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>   
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>   
 [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [方法 : SSL 証明書を使用してポートを構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)   
 [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [\<clientCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)   
 [Windows Server AppFabric のセキュリティ モデル](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)