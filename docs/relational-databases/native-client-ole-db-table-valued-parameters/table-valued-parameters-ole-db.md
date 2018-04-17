---
title: I parametri con valori di tabella (OLE DB) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
ms.assetid: 4298b73d-615b-4d28-9843-03b4d5fc489e
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a4d0cff3068093728cee9cebcdf8706e483dcbe6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="table-valued-parameters-ole-db"></a>Parametri con valori di tabella (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  In questa sezione viene illustrato il supporto per i parametri con valori di tabella nel provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Per ulteriori informazioni, vedere [Table-Valued Parameters &#40;SQL Server Native Client&#41;](../../relational-databases/native-client/features/table-valued-parameters-sql-server-native-client.md). Per un esempio, vedere [utilizzare parametri &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md).  
  
## <a name="remarks"></a>Osservazioni  
 Attualmente, è possibile inviare dati a riga multipla al server come parametri per una procedura con set di parametri (parametro DBPARAMS in **ICommand:: Execute**). Con i set di parametri, ogni elemento del set deve essere inviato al server in una richiesta di chiamata di procedura remota (RPC) separata. I parametri con valori di tabella forniscono funzionalità simili, ma offrono una maggiore integrazione con il server. Questa caratteristica determina la riduzione del numero di richieste RPC e l'abilitazione delle operazioni basate sul set nel server.  
  
 I parametri con valori di tabella sono supportati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider OLE DB come OLE DB **set di righe** oggetti. Qualsiasi **set di righe** oggetto stato fornito dal consumer (ovvero, le applicazioni client che usano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Provider Native Client OLE DB) come segnaposto per i parametri con valori di tabella. I parametri con valori di tabella vengono considerati come gli altri tipi di parametro di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client fornisce interfacce per gli schemi, l'associazione, la specifica, l'individuazione e la creazione.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Creazione di un set di righe di parametri con valori di tabella](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)  
  
-   [Individuazione dei tipi di parametro con valori di tabella](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md)  
  
-   [Esecuzione di comandi contenenti parametri con valori di tabella](../../relational-databases/native-client-ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md)  
  
-   [Inserimento di dati in parametri con valori di tabella](../../relational-databases/native-client-ole-db-table-valued-parameters/inserting-data-into-table-valued-parameters.md)  
  
-   [Set di righe dello schema modificati per i parametri con valori di tabella OLE DB](../../relational-databases/native-client-ole-db-table-valued-parameters/schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [Supporto dei tipi di parametro con valori di tabella OLE DB](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)  
  
-   [Supporto tipo di parametro con valori di tabella OLE DB &#40;metodi&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [Supporto tipo di parametro con valori di tabella OLE DB &#40;proprietà&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client & #40; OLE DB & #41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)   
 [Utilizzare i valori di tabella parametri & #40; OLE DB & #41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
