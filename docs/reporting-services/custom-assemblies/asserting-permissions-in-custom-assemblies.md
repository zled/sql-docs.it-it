---
title: L'asserzione delle autorizzazioni in assembly personalizzati | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- secure calls [Reporting Services]
- custom assemblies [Reporting Services], permissions
- permission sets [Reporting Services]
- asserting permissions
- permissions [Reporting Services], custom assemblies
- limited permission sets
- security configuration files [Reporting Services]
ms.assetid: 3afb9631-f15e-405e-990b-ee102828f298
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: e98c186e950b5f4186aea4057fb63c0f27eaf1b3
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="asserting-permissions-in-custom-assemblies"></a>Asserzione di autorizzazioni negli assembly personalizzati
  Per impostazione predefinita, il codice assembly personalizzato viene eseguito con la limitazione **esecuzione** set di autorizzazioni. In alcuni casi, potrebbe essere necessario implementare un assembly personalizzato per l'esecuzione di chiamate protette alle risorse protette all'interno del sistema di sicurezza (ad esempio un file o il Registro di sistema). A tale scopo, è necessario effettuare le operazioni seguenti:  
  
1.  Identificare le autorizzazioni esatte necessarie per il codice per effettuare la chiamata protetta. Se questo metodo fa parte di un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] libreria, queste informazioni devono essere inclusi nella documentazione del metodo.  
  
2.  Modificare i file di configurazione dei criteri del server di report per concedere le autorizzazioni necessarie all'assembly personalizzato. Per ulteriori informazioni sui file di configurazione dei criteri di sicurezza, vedere [tramite Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).  
  
3.  Eseguire l'asserzione delle autorizzazioni necessarie come parte del metodo nel quale viene effettuata la chiamata protetta. Questa operazione è necessaria perché il codice assembly personalizzato che viene chiamato dal server di report fa parte di report assembly host delle espressioni, che viene eseguito con **esecuzione** dell'autorizzazione per impostazione predefinita. Il **esecuzione** set di autorizzazioni consente al codice per l'esecuzione, ma non è consigliabile usare risorse protette.  
  
4.  Contrassegnare l'assembly personalizzato con **AllowPartiallyTrustedCallersAttribute** se è firmato con un nome sicuro. Questa operazione è necessaria perché gli assembly personalizzati vengono chiamati da un'espressione di report che fa parte di report assembly host delle espressioni, che, per impostazione predefinita, non viene concessa **FullTrust**; pertanto, è un chiamante "parzialmente attendibile". Per ulteriori informazioni, vedere [uso degli assembly personalizzati](../../reporting-services/custom-assemblies/using-strong-named-custom-assemblies.md).  
  
## <a name="implementing-a-secure-call"></a>Implementazione di una chiamata protetta  
 È possibile modificare i file di configurazione dei criteri per concedere autorizzazioni specifiche all'assembly. Se, ad esempio, si scrive un assembly personalizzato per gestire la conversione delle valute, potrebbe essere necessario leggere i tassi di cambio della valuta correnti da un file. Per recuperare le informazioni sulla frequenza, è necessario aggiungere un'ulteriore autorizzazioni di sicurezza, **FileIOPermission**, al set di autorizzazioni per l'assembly. Nel file di configurazione dei criteri è possibile inserire le seguenti voci aggiuntive:  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="CurrencyRatesFilePermissionSet"  
   Description="A special permission set that grants read access to my currency rates file.">  
      <IPermission class="FileIOPermission"  
         version="1"  
         Read="C:\CurrencyRates.xml"/>  
      <IPermission class="SecurityPermission"  
         version="1"  
         Flags="Execution, Assertion"/>  
</PermissionSet>  
```  
  
 Viene quindi aggiunto un gruppo di codice che fa riferimento a tale set di autorizzazioni:  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="CurrencyRatesFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\MSSQL\Reporting Services\ReportServer\bin\CurrencyConversion.dll"/>  
</CodeGroup>  
```  
  
 Per consentire al codice di acquisire l'autorizzazione appropriata, è necessaria l'asserzione dell'autorizzazione nel codice dell'assembly personalizzato. Se, ad esempio, si desidera aggiungere l'accesso in sola lettura a un file XML, C:\CurrencyRates.xml, è necessario aggiungere al metodo il codice seguente:  
  
```  
// C#  
FileIOPermission permission = new FileIOPermission(FileIOPermissionAccess.Read, @"C:\CurrencyRates.xml");  
try  
{  
   permission.Assert();  
   // Load the XML currency rates file  
   XmlDocument doc = new XmlDocument();  
   doc.Load(@"C:\CurrencyRates.xml");  
...  
```  
  
 È inoltre possibile aggiungere l'asserzione come attributo del metodo:  
  
```  
[FileIOPermissionAttribute(SecurityAction.Assert, Read=@"C:\CurrencyRates.xml")]  
```  
  
 Per ulteriori informazioni, vedere l'argomento relativo alla sicurezza di .NET Framework nella Guida per gli sviluppatori di .NET Framework.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di assembly personalizzati con i report](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
