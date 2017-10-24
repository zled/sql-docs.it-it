---
title: RightsEnum | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- RightsEnum
helpviewer_keywords:
- RightsEnum enumeration [ADOX]
ms.assetid: 55ee67c7-a583-42aa-849a-78264b4cb614
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ac335398b4895e01ece3324488d30bfd670fd140
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="rightsenum"></a>RightsEnum
Specifica i diritti o le autorizzazioni per un gruppo o utente su un oggetto.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adRightCreate**|16384 (& H4000)|L'utente o il gruppo dispone dell'autorizzazione per creare nuovi oggetti di questo tipo.|  
|**adRightDelete**|65536 (& H10000)|L'utente o il gruppo dispone dell'autorizzazione per eliminare i dati da un oggetto. Per gli oggetti, ad esempio **tabelle**, l'utente dispone dell'autorizzazione per eliminare i valori dei dati dal record.|  
|**adRightDrop**|256 (& H100)|L'utente o il gruppo dispone dell'autorizzazione per rimuovere gli oggetti dal catalogo. Ad esempio, **tabelle** può essere eliminato da un comando SQL DROP TABLE.|  
|**adRightExclusive**|512 (& H200)|L'utente o il gruppo dispone dell'autorizzazione per accedere all'oggetto in modo esclusivo.|  
|**adRightExecute**|536870912 (& H20000000)|L'utente o il gruppo dispone dell'autorizzazione per eseguire l'oggetto.|  
|**adRightFull**|268435456 (& H10000000)|L'utente o il gruppo ha tutte le autorizzazioni per l'oggetto.|  
|**adRightInsert**|32768 (& H8000)|L'utente o il gruppo dispone dell'autorizzazione per inserire l'oggetto. Per gli oggetti, ad esempio **tabelle**, l'utente dispone dell'autorizzazione per inserire dati nella tabella.|  
|**adRightMaximumAllowed**|33554432 (& H2000000)|L'utente o il gruppo è il numero massimo di autorizzazioni consentite dal provider. Autorizzazioni specifiche dipendono dal provider.|  
|**adRightNone**|0|L'utente o gruppo non dispone di autorizzazioni per l'oggetto.|  
|**adRightRead**|-2147483648 (& H80000000)|L'utente o il gruppo dispone dell'autorizzazione per leggere l'oggetto. Per gli oggetti, ad esempio [tabelle](../../../ado/reference/adox-api/table-object-adox.md), l'utente dispone dell'autorizzazione per leggere i dati nella tabella.|  
|**adRightReadDesign**|1024 (& H400)|L'utente o il gruppo dispone dell'autorizzazione per leggere la struttura per l'oggetto.|  
|**adRightReadPermissions**|131072 (& H20000)|L'utente o il gruppo può visualizzare, ma non modificare, le autorizzazioni specifiche per un oggetto nel catalogo.|  
|**adRightReference**|8192 (& H2000)|L'utente o il gruppo dispone dell'autorizzazione per fare riferimento all'oggetto.|  
|**adRightUpdate**|1073741824 (& H40000000)|L'utente o il gruppo dispone dell'autorizzazione per aggiornare l'oggetto. Per gli oggetti, ad esempio **tabelle**, l'utente dispone dell'autorizzazione per aggiornare i dati nella tabella.|  
|**adRightWithGrant**|4096 (& H1000)|L'utente o il gruppo dispone dell'autorizzazione per concedere autorizzazioni per l'oggetto.|  
|**adRightWriteDesign**|2048 (& H800)|L'utente o il gruppo dispone dell'autorizzazione per modificare la progettazione per l'oggetto.|  
|**adRightWriteOwner**|524288 (& H80000)|L'utente o il gruppo dispone dell'autorizzazione per modificare il proprietario dell'oggetto.|  
|**adRightWritePermissions**|262144 (& H40000)|L'utente o il gruppo è possibile modificare le autorizzazioni specifiche per un oggetto nel catalogo.|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Metodo GetPermissions (ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|[Metodo SetPermissions (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|

