---
title: Esecuzione di query XPath con spazi dei nomi (classi gestite SQLXML) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces property
- XPath queries [SQLXML], SQLXML Managed Classes
- queries [SQLXML], SQLXML Managed Classes
- XPath queries [SQLXML], namespaces
- Managed Classes [SQLXML], executing XPath queries
- SQLXML Managed Classes, executing XPath queries
- namespaces [SQLXML], XPath queries
ms.assetid: c6fc46d8-6b42-4992-a8f1-a8d4b8886e6e
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cc9e8e9c8d3ea5d35c30110d8b317152cd7c40aa
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2018
ms.locfileid: "51673400"
---
# <a name="executing-xpath-queries-with-namespaces-sqlxml-managed-classes"></a>Esecuzione di query XPath con spazi dei nomi (classi gestite SQLXML)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Le query XPath possono includere spazi dei nomi. Se gli elementi dello schema sono qualificati con spazio dei nomi, ovvero utilizzano uno spazio dei nomi di destinazione, le query XPath sullo schema devono specificare lo spazio dei nomi.  
  
 Poiché l'utilizzo del carattere jolly (*) non è supportato in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, è necessario specificare la query XPath utilizzando un prefisso di spazio dei nomi. Per risolvere il prefisso, utilizzare la proprietà di spazi dei nomi per specificare l'associazione dello spazio dei nomi.  
  
 Nell'esempio seguente, la query XPath specifica spazi dei nomi usando il carattere jolly (\*) e le funzioni di XPath Local e namespace-uri(). Questa query XPath restituisce tutti gli elementi in cui il nome locale è **dipendente** e lo spazio dei nomi URI **urn: myschema:Contacts**:  
  
```  
/*[local-name() = 'Contact' and namespace-uri() = 'urn:myschema:Contacts']  
```  
  
 In SQLXML 4.0 specificare questa query XPath con un prefisso di spazio dei nomi. Ad esempio **x: contattare**, dove **x** è il prefisso dello spazio dei nomi. Si consideri lo schema XSD seguente:  
  
```  
<schema xmlns="https://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:con="urn:myschema:Contacts"  
            targetNamespace="urn:myschema:Contacts">  
<complexType name="ContactType">  
  <attribute name="CID" sql:field="ContactID" type="ID"/>  
  <attribute name="FName" sql:field="FirstName" type="string"/>  
  <attribute name="LName" sql:field="LastName"/>   
</complexType>  
<element name="Contact" type="con:ContactType" sql:relation="Person.Contact"/>  
</schema>  
```  
  
 Poiché questo schema definisce lo spazio dei nomi di destinazione, una query XPath, ad esempio "Employee", eseguita sullo schema deve includere lo spazio dei nomi.  
  
 Nell'applicazione di esempio C# seguente viene eseguita una query XPath sullo schema XSD precedente (MySchema.xml). Per risolvere il prefisso, specificare l'associazione dello spazio dei nomi usando la proprietà di spazi dei nomi dell'oggetto SqlXmlCommand.  
  
> [!NOTE]  
>  Nel codice è necessario specificare il nome dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nella stringa di connessione.  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
      public static int testXPath()  
      {  
         //Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "x:Contact[@CID='1']";  
         cmd.CommandType = SqlXmlCommandType.XPath;  
         cmd.RootTag = "ROOT";  
         cmd.Namespaces = "xmlns:x='urn:myschema:Contacts'";  
         cmd.SchemaPath = "MySchema.xml";  
         using (Stream strm = cmd.ExecuteStream()){  
            using (StreamReader sr = new StreamReader(strm)){  
               Console.WriteLine(sr.ReadToEnd());  
            }  
         }  
         return 0;  
      }  
      public static int Main(String[] args)  
      {  
         testXPath();  
         return 0;  
      }  
   }  
```  
  
 Per testare questo esempio, è necessario che nel computer sia installato [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.  
  
### <a name="to-test-the-application"></a>Per testare l'applicazione  
  
1.  Salvare lo schema XSD (MySchema.xml) fornito in questo esempio in una cartella.  
  
2.  Salvare il codice C# (DocSample.cs) fornito in questo esempio nella stessa cartella nella quale viene archiviato lo schema. Se si archiviano i file in un'altra cartella, sarà necessario modificare il codice e specificare il percorso di directory appropriato per lo schema di mapping.  
  
3.  Compilare il codice. Per compilare il codice al prompt dei comandi, utilizzare:  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Viene creato un file eseguibile (DocSample.exe).  
  
4.  Al prompt dei comandi eseguire DocSample.exe.  
  
  
