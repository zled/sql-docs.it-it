---
title: Individuazione del tipo di parametro con valori di tabella | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
ms.assetid: f55818c2-ebb5-4cf6-8c0c-0da41f592560
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: af920c6ee746d064a1cb02d7ba60779dd6e8b22e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="table-valued-parameter-type-discovery"></a>Individuazione del tipo di parametro con valori di tabella
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il consumer, ovvero, ovvero le applicazioni client che usano il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Provider OLE DB Native, ovvero può individuare il tipo di ogni parametro di comando se il testo del comando è stato assegnato al Provider OLE DB. Una volta noto il tipo di un parametro con valori di tabella, il consumer può individuare le informazioni sui metadati per ogni singola colonna del parametro con valori di tabella.  
  
 Le informazioni sul tipo di parametri di routine è supportati da ICommandWithParameters:: GetParameterInfo per la maggior parte dei tipi di parametro. A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], con l'introduzione di tipi definiti dall'utente e la **xml** tipo di dati, il metodo GetParameterInfo non è sufficiente a questo scopo perché non è possibile fornire tipo definito dall'utente informazioni (nome, schema e catalogo) tramite ICommandWithParameters. Nuova interfaccia ISSCommandWithParameters, è stata definita per fornire informazioni estese sul tipo.  
  
 Per i parametri con valori di tabella, utilizzare anche l'interfaccia ISSCommandWithParameters per individuare informazioni dettagliate. Il client chiama ISSCommandWithParameters::GetParameterInfo dopo aver preparato l'oggetto comando. Per i parametri con valori di tabella, la *wType* membro della struttura DBPARAMINFO è impostato su DBTYPE_TABLE dal provider. Il *ulParamSize* campo della struttura DBPARAMINFO ha un valore pari a ~ 0.  
  
 Il consumer può quindi richiedere proprietà aggiuntive (nome di catalogo di tipo di parametro con valori di tabella, nome dello schema di tipo parametro con valori di tabella, il nome di tipo di parametro con valori di tabella, ordinamento delle colonne e le colonne predefinite) utilizzando ISSCommandWithParamters:: GetParameterProperties.  
  
 Dopo che il nome del tipo è noto, per recuperare le informazioni sulle singole colonne il consumer deve chiamare IOpenRowset::OpenRowsetor ottenere il set di righe DBSCHEMA_TABLE_TYPE_COLUMNS specificando il nome del tipo di parametro con valori di tabella come nome della tabella.  
  
## <a name="see-also"></a>Vedere anche  
 [Table-Valued Parameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utilizzare i valori di tabella parametri & #40; OLE DB & #41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
