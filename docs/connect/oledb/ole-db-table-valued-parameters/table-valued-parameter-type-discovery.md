---
title: Individuazione del tipo di parametro con valori di tabella | Documenti Microsoft
description: Con valori di tabella di rilevamento tipo parametro usando il Driver OLE DB per SQL Server
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
- table-valued parameters, type discovery
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 3edc0e15de25fc7b1fa4ab7d64826f6c3b65bdbc
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35306880"
---
# <a name="table-valued-parameter-type-discovery"></a>Individuazione del tipo di parametro con valori di tabella
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il consumer, vale a dire, l'applicazione client usando il Driver OLE DB per SQL Server, ovvero possono individuare il tipo di ogni parametro del comando se il testo del comando è stato assegnato al Provider OLE DB. Una volta noto il tipo di un parametro con valori di tabella, il consumer può individuare le informazioni sui metadati per ogni singola colonna del parametro con valori di tabella.  
  
 Le informazioni sul tipo di parametri di routine è supportati da ICommandWithParameters:: GetParameterInfo per la maggior parte dei tipi di parametro. A partire da [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], con l'introduzione di tipi definiti dall'utente e la **xml** tipo di dati, il metodo GetParameterInfo non è sufficiente a questo scopo perché non è possibile fornire tipo definito dall'utente informazioni (nome, schema e catalogo) tramite ICommandWithParameters. Nuova interfaccia ISSCommandWithParameters, è stata definita per fornire informazioni estese sul tipo.  
  
 Per i parametri con valori di tabella, utilizzare anche l'interfaccia ISSCommandWithParameters per individuare informazioni dettagliate. Il client chiama ISSCommandWithParameters::GetParameterInfo dopo aver preparato l'oggetto comando. Per i parametri con valori di tabella, la *wType* membro della struttura DBPARAMINFO è impostato su DBTYPE_TABLE dal provider. Il *ulParamSize* campo della struttura DBPARAMINFO ha un valore pari a ~ 0.  
  
 Il consumer può quindi richiedere proprietà aggiuntive (nome di catalogo di tipo di parametro con valori di tabella, nome dello schema di tipo parametro con valori di tabella, il nome di tipo di parametro con valori di tabella, ordinamento delle colonne e le colonne predefinite) utilizzando ISSCommandWithParamters:: GetParameterProperties.  
  
 Dopo che il nome del tipo è noto, per recuperare le informazioni sulle singole colonne il consumer deve chiamare IOpenRowset::OpenRowsetor ottenere il set di righe DBSCHEMA_TABLE_TYPE_COLUMNS specificando il nome del tipo di parametro con valori di tabella come nome della tabella.  
  
## <a name="see-also"></a>Vedere anche  
 [Table-Valued Parameters &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utilizzare parametri con valori di tabella &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
