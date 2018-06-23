---
title: Set di righe LINKEDSERVERS (OLE DB) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- LINKEDSERVERS rowset
- enumerating data sources [OLE DB]
ms.assetid: 2633fd8a-65e7-498d-9aed-8e4b1cca2381
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0901178fa2d99e4faf19c749026e2e1b1c17da7b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36156443"
---
# <a name="linkedservers-rowset-ole-db"></a>Set di righe LINKEDSERVERS (OLE DB)
  Il **LINKEDSERVERS** set di righe enumera le origini dati dell'organizzazione che possono partecipare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] query distribuite.  
  
 Il **LINKEDSERVERS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|SVR_NAME|DBTYPE_WSTR|Nome di un server collegato.|  
|SVR_PRODUCT|DBTYPE_WSTR|Produttore o altro nome che identifica il tipo di archivio dati rappresentato dal nome del server collegato.|  
|SVR_PROVIDERNAME|DBTYPE_WSTR|Nome descrittivo del provider OLE DB impiegato per utilizzare dati dal server.|  
|SVR_DATASOURCE|DBTYPE_WSTR|Stringa OLE DB DBPROP_INIT_DATASOURCE utilizzata per acquisire un'origine dati dal provider.|  
|SVR_PROVIDERSTRING|DBTYPE_WSTR|Valore OLE DB DBPROP_INIT_PROVIDERSTRING utilizzato per acquisire un'origine dati dal provider.|  
|SVR_LOCATION|DBTYPE_WSTR|Stringa OLE DB DBPROP_INIT_LOCATION utilizzata per acquisire un'origine dati dal provider.|  
  
 Il set di righe viene ordinato su SRV_NAME e una singola restrizione è supportata su SRV_NAME.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di set di righe dello schema &#40;OLE DB&#41;](schema-rowset-support-ole-db.md)  
  
  