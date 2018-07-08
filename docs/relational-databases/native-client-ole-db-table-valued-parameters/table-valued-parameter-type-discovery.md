---
title: Individuazione del tipo di parametro con valori di tabella | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
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
ms.openlocfilehash: 373e2c17254b55ed351695286b9a4a5d03f2d47c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420050"
---
# <a name="table-valued-parameter-type-discovery"></a>Individuazione del tipo di parametro con valori di tabella
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Il consumer, vale a dire, le applicazioni client che usano il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client Provider OLE DB Native, ovvero può individuare il tipo di ogni parametro del comando se il testo del comando è stato assegnato per il Provider OLE DB. Una volta noto il tipo di un parametro con valori di tabella, il consumer può individuare le informazioni sui metadati per ogni singola colonna del parametro con valori di tabella.  
  
 Le informazioni sul tipo di parametri di routine è supportati da ICommandWithParameters:: GetParameterInfo per la maggior parte dei tipi di parametro. A partire [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], con l'introduzione di tipi definiti dall'utente e la **xml** tipo di dati, il metodo GetParameterInfo non era sufficiente per questo scopo perché non era possibile indicare tipo definito dall'utente informazioni (nome, schema e catalogo) tramite ICommandWithParameters. È stata definita una nuova interfaccia ISSCommandWithParameters, per fornire informazioni estese sul tipo.  
  
 Per i parametri con valori di tabella, utilizziamo inoltre l'interfaccia ISSCommandWithParameters per individuare informazioni dettagliate. Il client chiama ISSCommandWithParameters::GetParameterInfo dopo aver preparato l'oggetto comando. Per parametri con valori di tabella, la *wType* membro della struttura DBPARAMINFO viene impostato su DBTYPE_TABLE dal provider. Il *ulParamSize* campo della struttura DBPARAMINFO ha un valore di ~ 0.  
  
 Il consumer può quindi richiedere proprietà aggiuntive (nome di catalogo di tipo di parametro con valori di tabella, nome dello schema del tipo parametro con valori di tabella, nome del tipo di parametro con valori di tabella, ordinamento delle colonne e colonne predefinite) mediante ISSCommandWithParamters:: GetParameterProperties.  
  
 Dopo che il nome del tipo è noto, per recuperare le informazioni sulle singole colonne il consumer deve chiamare IOpenRowset::OpenRowsetor ottenere il set di righe DBSCHEMA_TABLE_TYPE_COLUMNS specificando il nome del tipo di parametro con valori di tabella come nome della tabella.  
  
## <a name="see-also"></a>Vedere anche  
 [I parametri con valori di tabella &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Usare parametri con valori di tabella &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
