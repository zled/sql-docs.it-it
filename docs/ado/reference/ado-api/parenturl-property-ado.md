---
title: "Proprietà ParentURL (ADO) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Record::ParentURL
helpviewer_keywords:
- ParentURL property [ADO]
ms.assetid: 65120ce6-3900-4cd4-b322-3b9816d74737
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eca04999eece256ef22503c4d227ffcec297c79a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="parenturl-property-ado"></a>Proprietà ParentURL (ADO)
Indica una stringa URL assoluto che punta all'elemento padre [Record](../../../ado/reference/ado-api/record-object-ado.md) corrente **Record** oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **stringa** valore che indica l'URL dell'elemento padre **Record**.  
  
## <a name="remarks"></a>Osservazioni  
 Il **ParentURL** proprietà dipende dall'origine utilizzata per aprire la **Record** oggetto. Ad esempio, il **Record** può essere aperto con un'origine che contiene un nome di percorso relativo di una directory a cui fa riferimento il [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) proprietà.  
  
 Si supponga che "second" è una cartella inclusa in "first". Aprire il **Record** oggetto utilizzando la sintassi seguente:  
  
```  
record.ActiveConnection = "http://first"  
record.Open "second"  
```  
  
 A questo punto, il valore di `the` **ParentURL** proprietà `"http://first"`, la stessa come **ActiveConnection**.  
  
 L'origine può anche essere un URL assoluto, ad esempio, `"http://first/second"`. Il **ParentURL** proprietà viene quindi `"http://first"`, il livello superiore `"second"`.  
  
 Questa proprietà può essere un valore null se:  
  
-   È presente alcun padre per l'oggetto corrente. ad esempio, se il **Record** oggetto rappresenta la radice di una directory.  
  
-   Il **Record** oggetto rappresenta un'entità che non può essere specificata con un URL.  
  
 Questa proprietà è di sola lettura.  
  
> [!NOTE]
>  Questa proprietà è supportata solo dai provider di origine di documento, ad esempio il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [record e campi specificati dal provider](../../../ado/guide/data/records-and-provider-supplied-fields.md).  
  
> [!NOTE]
>  Gli URL che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
> [!NOTE]
>  Se il record corrente contiene un record di dati da un oggetto ADO **Recordset**, l'accesso al **ParentURL** proprietà causa un errore in fase di esecuzione, che indica che non è possibile alcun URL.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
