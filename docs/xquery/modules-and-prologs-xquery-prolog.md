---
title: Prologo XQuery | Documenti Microsoft
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- XQuery, prolog
- prolog
- namespaces [XQuery]
- default namespace declarations
ms.assetid: 03924684-c5fd-44dc-8d73-c6ab90f5e069
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bb14308461be8c13e8a683ae842a63647191c9e0
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="modules-and-prologs---xquery-prolog"></a>Moduli e prologhi - prologo XQuery
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Una query XQuery è composta da un prologo e da un corpo. Il prologo include una serie di dichiarazioni e di definizioni che contribuiscono a creare l'ambiente necessario per l'elaborazione della query. In SQL Server, il prologo della query XQuery può contenere dichiarazioni dello spazio dei nomi. Il corpo della query XQuery è composto da una sequenza di espressioni che specificano il risultato della query desiderato.  
  
 Ad esempio, la query XQuery seguente viene eseguita sulla colonna Instructions di **xml** tipo che contiene le istruzioni di produzione in formato XML. La query recupera le istruzioni di produzione per il centro di lavorazione `10`. Il `query()` metodo il **xml** tipo di dati viene utilizzato per specificare l'espressione XQuery.  
  
```  
SELECT Instructions.query('declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";           
    /AWMI:root/AWMI:Location[@LocationID=10]  
') AS Result   
FROM  Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Il prologo include una dichiarazione di prefisso (AWMI) dello spazio dei nomi, `(namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";`.  
  
-   La parola chiave `declare namespace` definisce un prefisso dello spazio dei nomi che viene utilizzato successivamente nel corpo della query.  
  
-   `/AWMI:root/AWMI:Location[@LocationID="10"]` è il corpo della query.  
  
## <a name="namespace-declarations"></a>Dichiarazioni dello spazio dei nomi  
 Una dichiarazione dello spazio dei nomi definisce un prefisso e lo associa a un URI (Uniform Resource Identifier) dello spazio dei nomi, come illustrato nella query seguente. Nella query, `CatalogDescription` è un **xml** colonna di tipo.  
  
 Quando si esegue la query XQuery sulla colonna, il prologo della query specifica la dichiarazione `declare namespace` tramite la quale il prefisso `PD`, ovvero la descrizione del prodotto, viene associato all'URI dello spazio dei nomi. Questo prefisso viene quindi utilizzato nel corpo della query in sostituzione dell'URI dello spazio dei nomi. I nodi del codice XML risultante sono nello spazio dei nomi associato all'URI dello spazio dei nomi.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
         /PD:ProductDescription/PD:Summary   
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Per migliorare la leggibilità della query è possibile dichiarare gli spazi dei nomi utilizzando WITH XMLNAMESPACES anziché dichiarare l'associazione tra il prefisso e lo spazio dei nomi nel prologo della query utilizzando `declare namespace`.  
  
```  
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD)  
  
SELECT CatalogDescription.query('  
         /PD:ProductDescription/PD:Summary   
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Per ulteriori informazioni, vedere, [aggiungere spazi dei nomi alle query con WITH XMLNAMESPACES](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md).  
  
### <a name="default-namespace-declaration"></a>Dichiarazione dello spazio dei nomi predefinito  
 Anziché dichiarare un prefisso dello spazio dei nomi utilizzando la dichiarazione `declare namespace`, è possibile utilizzare la dichiarazione `declare default element namespace` per associare uno spazio dei nomi predefinito ai nomi degli elementi. In questo caso, non è necessario specificare un prefisso.  
  
 Nell'esempio seguente, l'espressione di percorso nel corpo della query non specifica un prefisso dello spazio dei nomi. Per impostazione predefinita, tutti i nomi degli elementi appartengono allo spazio dei nomi predefinito specificato nel prologo.  
  
```  
SELECT CatalogDescription.query('  
     declare default element namespace  "http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
        /ProductDescription/Summary   
    ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID=19   
```  
  
 Per dichiarare uno spazio dei nomi predefinito è possibile utilizzare WITH XMLNAMESPACES:  
  
```  
WITH XMLNAMESPACES (DEFAULT 'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription')  
SELECT CatalogDescription.query('  
        /ProductDescription/Summary   
    ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID=19   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere spazi dei nomi alle query con WITH XMLNAMESPACES](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)  
  
  
