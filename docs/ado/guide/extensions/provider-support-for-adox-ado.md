---
title: Supporto del provider per ADOX (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ADOX provider support [ADO]
ms.assetid: 64234ce5-dc46-4c8a-a316-61956b6b9abb
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 48f0e58ce794f53a123267b664e8c4c933976fe7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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
