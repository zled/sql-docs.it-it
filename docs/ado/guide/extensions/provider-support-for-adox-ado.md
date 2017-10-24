---
title: Supporto del provider per ADOX (ADO) | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADOX provider support [ADO]
ms.assetid: 64234ce5-dc46-4c8a-a316-61956b6b9abb
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b15df02c70e2dcdc2efb2ba468b76219a233d65a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="provider-support-for-adox-ado"></a>Supporto del provider per ADOX (ADO)
Alcune caratteristiche di ADOX non sono supportati, a seconda del provider di dati OLE DB. ADOX è completamente supportato con la [il Provider OLE DB per Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md). Funzionalità non supportate con il [il Provider Microsoft OLE DB per SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), [Provider Microsoft OLE DB per ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md), o [Provider Microsoft OLE DB per Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md) sono elencati nelle tabelle seguenti. ADOX non è supportata da tutti gli altri provider Microsoft OLE DB.  
  
## <a name="microsoft-ole-db-provider-for-sql-server"></a>Provider Microsoft OLE DB per SQL Server  
  
|Oggetto o raccolta|Limitazione dell'utilizzo|  
|--------------------------|-----------------------|  
|**Tabelle** raccolta|Proprietà sono di lettura/scrittura prima della creazione di oggetti e di sola lettura quando si fa riferimento un oggetto esistente.|  
|**Viste** raccolta|**Viste** non è supportata.|  
|**Procedure** raccolta|Il **Append** e **eliminare** metodi non sono supportati.|  
|**Procedura** oggetto|Il **comando** proprietà non è supportata.|  
|**Le chiavi** raccolta|Il **Append** e **eliminare** metodi non sono supportati.|  
|**Gli utenti** raccolta|**Gli utenti** non è supportata.|  
|**Gruppi** raccolta|**Gruppi** non è supportata.|  
  
## <a name="microsoft-ole-db-provider-for-odbc"></a>Provider Microsoft OLE DB per ODBC  
  
|Oggetto o raccolta|Limitazione dell'utilizzo|  
|--------------------------|-----------------------|  
|**Catalogo** oggetto|Il **crea** metodo non è supportato.|  
|**Tabelle** raccolta|Il **Append** e **eliminare** metodi non sono supportati. Proprietà sono di lettura/scrittura prima della creazione di oggetti e di sola lettura quando si fa riferimento un oggetto esistente.|  
|**Procedure** raccolta|Il **Append** e **eliminare** metodi non sono supportati.|  
|**Procedura** oggetto|Il **comando** proprietà non è supportata.|  
|**Gli indici** raccolta|Il **Append** e **eliminare** metodi non sono supportati.|  
|**Le chiavi** raccolta|Il **Append** e **eliminare** metodi non sono supportati.|  
|**Gli utenti** raccolta|**Gli utenti** non è supportata.|  
|**Gruppi** raccolta|**Gruppi** non è supportata.|  
  
## <a name="microsoft-ole-db-provider-for-oracle"></a>Provider OLE DB per Oracle  
  
|Oggetto o raccolta|Limitazione dell'utilizzo|  
|--------------------------|-----------------------|  
|**Catalogo** oggetto|Il **crea** metodo non è supportato.|  
|**Tabelle** raccolta|Il **Append** e **eliminare** metodi non sono supportati. Proprietà sono di lettura/scrittura prima della creazione di oggetti e di sola lettura quando si fa riferimento un oggetto esistente.|  
|**Viste** raccolta|Il **Append** e **eliminare** metodi non sono supportati.|  
|**Visualizzazione** oggetto|Il **comando** proprietà non è supportata.|  
|**Procedure** oggetto|Il **Append** e **eliminare** metodi non sono supportati.|  
|**Procedura** oggetto|Il **comando** proprietà non è supportata.|  
|**Gli indici** raccolta|Il **Append** e **eliminare** metodi non sono supportati.|  
|**Le chiavi** raccolta|Il **Append** e **eliminare** metodi non sono supportati.|  
|**Gli utenti** raccolta|**Gli utenti** non è supportata.|  
|**Gruppi** raccolta|**Gruppi** non è supportata.|

