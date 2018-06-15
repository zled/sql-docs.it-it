---
title: Inserimento di dati in parametri con valori di tabella | Documenti Microsoft
description: Tramite il Driver OLE DB per SQL Server per inserire dati in parametri con valori di tabella
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, inserting data into
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 8806d301eeaa25f00b8e3a3fe3553fb08e7005a5
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35306460"
---
# <a name="inserting-data-into-table-valued-parameters"></a>Inserimento di dati in parametri con valori di tabella
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il Driver OLE DB per SQL Server supporta due modelli per il consumer può specificare i dati per righe di parametri con valori di tabella: un modello push e un modello di pull. Un esempio che illustra il modello pull è disponibile. vedere [esempi di programmazione dati di SQL Server](http://msftdpprodsamples.codeplex.com/).  
  
> [!NOTE]  
>  Una colonna di parametri con valori di tabella deve includere valori non predefiniti in tutte le righe o valori predefiniti in tutte le righe. Non è possibile che vi siano valori predefiniti in alcune righe e non in altre. Nelle associazioni di parametri con valori di tabella, pertanto, gli unici valori di stato consentiti per i dati di colonna dei set di righe di parametri con valori di tabella sono DBSTATUS_S_ISNULL e DBSTATUS_S_OK. DBSTATUS_S_DEFAULT comporteranno un errore e il valore di stato associato verrà impostato su DBSTATUS_E_BADSTATUS.  
  
## <a name="push-model-loads-all-table-valued-paremeter-data-in-memory"></a>Modello push (carica in memoria tutti i dati dei parametri con valori di tabella)  
 Il modello push è simile all'utilizzo di set di parametri (ovvero, il parametro DBPARAMS in ICommand:: Execute). Il modello push viene utilizzato solo se vengono utilizzati gli oggetti di set di righe di parametri con valori di tabella senza un'implementazione personalizzata di interfacce IRowset. Il modello push è consigliabile quando il numero di righe nel set di righe di parametri con valori di tabella è ridotto e non si prevede un utilizzo elevato della memoria nell'applicazione. Questo modello è più semplice del modello pull, in quanto non richiede altre funzionalità dall'applicazione consumer rispetto a quelle comuni normalmente utilizzate nelle applicazioni OLE DB tipiche.  
  
 In genere il consumer fornisce al provider tutti i dati dei parametri con valori di tabella prima di eseguire un comando. Per fornire i dati, il consumer popola un oggetto set di righe di parametri con valori di tabella per ogni parametro con valori di tabella. L'oggetto set di righe di parametri con valori di tabella espone operazioni Insert, Set e Delete per il set di righe che verranno utilizzate dal consumer per modificare i dati dei parametri con valori di tabella. Il provider recupererà i dati da questo oggetto set di righe di parametri con valori di tabella in fase di esecuzione.  
  
 Quando al consumer viene fornito un oggetto set di righe di parametri con valori di tabella, il consumer può elaborarlo come oggetto set di righe. Il consumer può ottenere le informazioni sul tipo di ogni colonna (tipo, lunghezza massima, precisione e scala) utilizzando il metodo di interfaccia IColumnsInfo:: GetColumnInfo o IColumnsRowset::. Il consumer crea quindi una funzione di accesso per specificare le associazioni per i dati. Il passaggio successivo consiste nell'inserire righe di dati nel set di righe di parametri con valori di tabella. Questa operazione può essere eseguita tramite IRowsetChange:: InsertRow. IRowsetChange:: SetData o IRowsetChange:: può essere utilizzato anche per l'oggetto set di righe di parametri con valori di tabella se è necessario modificare i dati. Gli oggetti set di righe di parametri con valori di tabella sono soggetti a conteggio dei riferimenti, analogamente agli oggetti di flusso.  
  
 Se si utilizza IColumnsRowset::, esisterà le chiamate successive ai metodi IRowset:: GetNextRows IRowset:: GetData e IRowset:: ReleaseRows nell'oggetto set di righe della colonna risultante.  
  
 Dopo che il Driver OLE DB per SQL Server inizia l'esecuzione del comando, i valori dei parametri con valori di tabella verranno recuperati da questo oggetto di set di righe di parametri con valori di tabella e inviati al server.  
  
 Il modello push richiede attività minime da parte del consumer, ma utilizza una maggiore quantità di memoria rispetto al modello pull, in quanto tutti i dati dei parametri con valori di tabella devono essere presenti in memoria in fase di esecuzione.  
  
## <a name="pull-model-obtaining-table-valued-parameter-data-on-demand-from-the-consumer"></a>Modello pull (recupero di dati dei parametri con valori di tabella su richiesta dal consumer)  
 Il modello pull è utile per due scenari:  
  
-   Per eseguire il flusso di righe.  
  
-   Se si utilizza un set di righe di un altro provider come valore di parametro con valori di tabella.  
  
 Nel modello pull il consumer fornisce dati su richiesta al provider. Utilizzare questo approccio se nell'applicazione vengono eseguiti molti inserimenti di dati, e i dati del set di righe di parametri con valori di tabella in memoria comporterebbero un eccessivo accesso alla memoria. Se si utilizzano più provider OLE DB, il modello pull del consumer consente al consumer di fornire qualsiasi oggetto set di righe come valore di parametro con valori di tabella.  
  
 Per utilizzare il modello pull, i consumer devono specificare l'implementazione personalizzata di un oggetto set di righe. Quando si utilizza il modello pull con set di righe di parametri con valori di tabella (CLSID_ROWSET_TVP), il consumer viene richiesto di aggregare l'oggetto set di righe di parametri con valori di tabella esposte dal provider tramite il ITableDefinitionWithConstraints:: Metodo CreateTableWithConstraints o IOpenRowset:: OPENROWSET. Il comportamento previsto per l'oggetto consumer consiste esclusivamente nel sostituire l'implementazione dell'interfaccia IRowset. È necessario sostituire le funzioni seguenti:  
  
-   IRowset::GetNextRows  
  
-   IRowset::AddRefRows  
  
-   IRowset::GetData  
  
-   IRowset:: ReleaseRows  
  
-   IRowset:: RestartPosition  
  
 Il Driver OLE DB per SQL Server verrà letta una o più righe alla volta dal consumer oggetto set di righe per supportare il comportamento di flusso in parametri con valori di tabella. Ad esempio, l'utente potrebbe avere i dati dei set di righe di parametri con valori di tabella su disco (non in memoria) e implementa la funzionalità per leggere i dati dal disco se richiesto dal Driver OLE DB per SQL Server.  
  
 Il consumer comunicherà il formato dei dati per il Driver OLE DB per SQL Server utilizzando IAccessor:: CreateAccessor per l'oggetto set di righe di parametri con valori di tabella. Durante la lettura dei dati dal buffer del consumer, il provider verifica che tutte le colonne accessibili in scrittura e non predefinite siano disponibili tramite almeno un handle della funzione di accesso e utilizza gli handle corrispondenti per leggere i dati delle colonne. Per evitare ambiguità, deve essere una corrispondenza tra una colonna di set di righe di parametri con valori di tabella e un'associazione. Associazioni duplicate alla stessa colonna comporteranno un errore. Inoltre, ogni funzione di accesso deve disporre di *iOrdinal* membri DBBindings in sequenza. Vi sono il numero di chiamate a IRowset:: GetData come il numero di funzioni di accesso per ogni riga e l'ordine delle chiamate sarà basato sull'ordine del *iOrdinal* valore da valori inferiori a quelli superiori.  
  
 Il comportamento previsto del provider consiste nell'implementare la maggior parte delle interfacce esposte dall'oggetto set di righe di parametri con valori di tabella. Il consumer implementerà un oggetto set di righe con interfacce minime (IRowset). A causa dell'aggregazione nascosta, le interfacce obbligatorie rimanenti dell'oggetto set di righe verranno implementate dall'oggetto set di righe di parametri con valori di tabella.  
  
 Per qualsiasi altro oggetto set di righe, ad esempio gli oggetti set di righe ottenuti per qualunque provider OLE DB, il set di righe fornito dal consumer deve implementare tutte le interfacce dell'oggetto set di righe obbligatorie in base a quanto indicato dalla specifica OLE DB.  
  
 Durante la fase di esecuzione, il Driver OLE DB per SQL Server richiamerà l'oggetto set di righe per recuperare righe e leggere i dati di colonna.  
  
## <a name="see-also"></a>Vedere anche  
 [Table-Valued Parameters &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utilizzare parametri con valori di tabella &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
