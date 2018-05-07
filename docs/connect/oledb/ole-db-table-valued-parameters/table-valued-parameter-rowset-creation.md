---
title: La creazione dei set di righe di parametri con valori di tabella | Documenti Microsoft
description: Creazione di set di righe di parametro con valori di tabella statica e dinamica
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, rowset creation
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 0bfd6f54e374c77268641e151f738efa8a2385b5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="table-valued-parameter-rowset-creation"></a>Creazione di un set di righe di parametri con valori di tabella
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Sebbene i consumer siano in grado di fornire qualsiasi oggetto set di righe per i parametri con valori di tabella, vengono implementati gli oggetti set di righe tipici rispetto agli archivi dati di back-end, con conseguente limitazione delle prestazioni. Per questo motivo, il Driver OLE DB per SQL Server consente agli utenti di creare un oggetto set di righe specifico nella parte superiore di dati in memoria. Questo oggetto set di righe speciale in memoria rappresenta un nuovo oggetto COM definito set di righe di parametri con valori di tabella. Tale oggetto fornisce funzionalità simili ai set di parametri.  
  
 Gli oggetti set di righe di parametri con valori di tabella vengono creati in modo esplicito dal consumer per i parametri di input tramite più interfacce a livello di sessione. Viene rilevata un'istanza di un oggetto set di righe di parametri con valori di tabella per ogni parametro con valori di tabella. Il consumer può creare gli oggetti set di righe di parametri con valori di tabella fornendo le informazioni sui metadati già note (scenario statico) o individuandole tramite le interfacce del provider (scenario dinamico). Nelle sezioni seguenti vengono descritti questi due scenari.  
  
## <a name="static-scenario"></a>Scenario statico  
 Quando le informazioni sul tipo è noto, il consumer utilizza ITableDefinitionWithConstraints::CreateTableWithConstraints per creare un'istanza di un oggetto set di righe di parametri con valori di tabella che corrisponde a un parametro con valori di tabella.  
  
 Il *guid* campo (*pTableID* parametro) contiene il GUID speciale (CLSID_ROWSET_TVP). Il *pwszName* membro contiene il nome del tipo di parametro con valori di tabella che l'utente desidera creare un'istanza. Il *eKind* campo verrà impostato su DBKIND_GUID_NAME. Questo nome è obbligatorio quando l'istruzione SQL ad hoc; il nome è facoltativo se si tratta di una chiamata di routine.  
  
 Per l'aggregazione, il consumer passa il *pUnkOuter* parametro con l'interfaccia IUnknown di controllo.  
  
 Le proprietà dell'oggetto set di righe di parametri con valori di tabella sono di sola lettura, pertanto il consumer non è quello previsto per impostare le proprietà nel *rgPropertySets*.  
  
 Per il *rgPropertySets* membro di ogni struttura DBCOLUMNDESC, il consumer può specificare proprietà aggiuntive per ogni colonna. Queste proprietà appartengono al set di proprietà DBPROPSET_SQLSERVERCOLUMN. Tali proprietà consentono di specificare le impostazioni predefinite e calcolate per ogni colonna. Supportano inoltre le proprietà esistenti della colonna, ad esempio nullability e identity.  
  
 Per recuperare le informazioni corrispondenti da un oggetto set di righe di parametri con valori di tabella, il consumer utilizza IRowsetInfo:: GetProperties.  
  
 Per recuperare informazioni su null, univoco, calcolata e aggiornare lo stato di ogni colonna, il consumer può utilizzare IColumnsRowset:: GetColumnsRowset o IColumnsInfo:: GetColumnInfo. Questi metodi forniscono informazioni dettagliate su ogni colonna del set di righe di parametri con valori di tabella.  
  
 Il consumer specifica il tipo di ogni colonna del parametro con valori di tabella, È simile al modo in cui sono specificate colonne quando viene creata una tabella [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il consumer Ottiene un oggetto set di righe di parametri con valori di tabella dal Driver OLE DB per SQL Server tramite il *ppRowset* parametro di output.  
  
## <a name="dynamic-scenario"></a>Scenario dinamico  
 Quando il consumer non dispone di informazioni sul tipo, è necessario utilizzare IOpenRowset:: OPENROWSET per creare istanze di oggetti set di righe di parametri con valori di tabella. L'unica informazione che il consumer deve fornire al provider è il nome del tipo.  
  
 In questo scenario, il provider ottiene le informazioni sul tipo relative a un oggetto set di righe di parametri con valori di tabella dal server per conto del consumer.  
  
 Il *pTableID* e *pUnkOuter* parametri devono essere impostati come nello scenario statico. Il Driver OLE DB per SQL Server Ottiene le informazioni sul tipo (informazioni sulle colonne e vincoli) dal server, quindi restituire un oggetto set di righe di parametri con valori di tabella tramite il *ppRowset* parametro. Questa operazione richiede la comunicazione con il server e pertanto non viene eseguita, nonché lo scenario statico. Lo scenario dinamico funziona solo con le chiamate di procedura con parametri.  
  
## <a name="see-also"></a>Vedere anche  
 [Table-Valued Parameters &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utilizzare i valori di tabella parametri & #40; OLE DB & #41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
