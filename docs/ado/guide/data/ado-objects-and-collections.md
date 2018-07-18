---
title: Raccolte e gli oggetti ADO | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, objects and collections
ms.assetid: 7a745aae-9372-49b6-8dae-b9c93e5f3216
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d8b1967071b5dc420577ecbee3f1b124d917057
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271380"
---
# <a name="ado-objects-and-collections"></a>Raccolte e gli oggetti ADO
ADO è costituito da nove oggetti seguenti e quattro raccolte.  
  
|Oggetto o raccolta|Description|  
|--------------------------|-----------------|  
|**Connessione** oggetto|Rappresenta una sessione univoca con un'origine dati. Nel caso di un sistema di database client/server, potrebbe essere equivalente a una connessione di rete effettiva al server. A seconda della funzionalità supportata dal provider, alcuni insiemi, metodi o proprietà di un **connessione** oggetto potrebbe non essere disponibile.|  
|**Command**|Utilizzato per definire un comando specifico, ad esempio una query SQL, può essere eseguito su un'origine dati.|  
|**Recordset** oggetto|Rappresenta l'intero set di record da una tabella di base o i risultati di un comando eseguito. Tutti **Recordset** oggetti è costituito da record (righe) e campi (colonne).|  
|**Record** oggetto|Rappresenta una singola riga di dati, da un **Recordset** o dal provider. Questo record può rappresentare un record di database o un altro tipo di oggetto, ad esempio un file o directory, a seconda del provider.|  
|**Flusso** oggetto|Rappresenta un flusso di dati di testo o binario. Ad esempio, un documento XML può essere caricato in un flusso per il comando di input o restituito da alcuni provider, come i risultati di una query. Oggetto **flusso** oggetto può essere utilizzato per modificare i campi o record contenenti tali flussi di dati.|  
|**Parametro** oggetto|Rappresenta un parametro o un argomento associato a un **comando** oggetto, in base a una stored procedure o query con parametri.|  
|**Campo** oggetto|Rappresenta una colonna di dati con un tipo di dati. Ogni **campo** oggetto corrisponde a una colonna di **Recordset**.|  
|**Proprietà** oggetto|Rappresenta una caratteristica di un oggetto ADO definito dal provider. Gli oggetti ADO hanno due tipi di proprietà: incorporato e dinamici. Tali proprietà predefinite sono implementate in ADO e immediatamente disponibili per qualsiasi nuovo oggetto. Il **proprietà** oggetto è un contenitore per le proprietà dinamiche, definito dal provider sottostante.|  
|**Error**|Contiene informazioni sugli errori di accesso ai dati relativi a una singola operazione che include il provider.|  
|**Campi** raccolta|Contiene tutti i **campo** gli oggetti di un **Recordset** o **Record** oggetto.|  
|**Proprietà** raccolta|Contiene tutti i **proprietà** oggetti per un'istanza specifica di un oggetto.|  
|**I parametri** raccolta|Contiene tutti i **parametro** gli oggetti di un **comando** oggetto.|  
|**Errori** raccolta|Contiene tutti i **errore** gli oggetti creati in risposta a un singolo errore correlato al provider.|  
  
## <a name="see-also"></a>Vedere anche  
 [Modello a oggetti ADO](../../../ado/reference/ado-api/ado-object-model.md)
