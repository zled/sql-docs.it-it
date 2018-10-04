---
title: MSmerge_conflicts_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_conflicts_info_TSQL
- MSmerge_conflicts_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_conflicts_info system table
ms.assetid: 6b76ae96-737a-4000-a6b6-fcc8772c2af4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 34dd7496d514db14399134eb7ffe222af7251f95
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737729"
---
# <a name="msmergeconflictsinfo-transact-sql"></a>MSmerge_conflicts_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSmerge_conflicts_info** tabella tiene traccia dei conflitti che si verificano durante la sincronizzazione di una sottoscrizione a una pubblicazione di tipo merge. I dati di riga non confermata i conflitti vengono archiviati nel [MSmerge_conflict_publication_article](../../relational-databases/system-tables/msmerge-conflict-publication-article-transact-sql.md) tabella per l'articolo in cui si è verificato il conflitto. Questa tabella è archiviata nel database di pubblicazione del server di pubblicazione e nel database di sottoscrizione del Sottoscrittore.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Nome alternativo della tabella pubblicata.|  
|**rowguid**|**uniqueidentifier**|Identificatore della riga in conflitto.|  
|**origin_datasource**|**nvarchar(255)**|Nome del database in cui ha avuto origine la modifica in conflitto.|  
|**conflict_type**|**int**|Tipo di conflitto che si è verificato. I possibili valori sono i seguenti.<br /><br /> **1** = conflitto aggiornamento: il conflitto viene rilevato a livello di riga.<br /><br /> **2** = conflitto aggiornamento colonna: il conflitto viene rilevato a livello di colonna.<br /><br /> **3** = conflitto aggiornamento / eliminazione: l'eliminazione prevale nel conflitto.<br /><br /> **4** = conflitto aggiornamento / eliminazione: il rowguid eliminato che perde nel conflitto viene registrato in questa tabella.<br /><br /> **5** = caricare inserimento non riuscito: l'inserimento dal sottoscrittore non può essere applicato nel server di pubblicazione.<br /><br /> **6** = scaricare inserimento non riuscito: l'inserimento dal server di pubblicazione non può essere applicato nel Sottoscrittore.<br /><br /> **7** = caricare eliminazione non riuscita: non è possibile caricare l'eliminazione dal Sottoscrittore al server di pubblicazione.<br /><br /> **8** = scaricare eliminazione non riuscita: non è stato possibile scaricare l'eliminazione dal server di pubblicazione al sottoscrittore.<br /><br /> **9** = caricamento aggiornamento non riuscito: Impossibile applicare l'aggiornamento nel Sottoscrittore nel server di pubblicazione.<br /><br /> **10** = Scarica aggiornamento non riuscito: non è stato possibile applicare l'aggiornamento nel server di pubblicazione al sottoscrittore.<br /><br /> **11** = risoluzione<br /><br /> **12** = logico Record di aggiornamento / eliminazione: il record logico eliminato non prioritario viene registrato in questa tabella.<br /><br /> **13** = logico Record conflitto aggiornamento/inserimento: inserimento di un record logico è in conflitto con un aggiornamento.<br /><br /> **14** = logico Record conflitto aggiornamento / eliminazione: il record logico aggiornato non prioritario viene registrato in questa tabella.|  
|**reason_code**|**int**|Codice di errore che può essere sensibile al contesto. In caso di conflitti aggiornamento-aggiornamento e aggiornamento-eliminazione, il valore usato per questa colonna è quello utilizzato per il **conflict_type**. Per i conflitti di modifica non riuscita, tuttavia, il codice motivo è l'errore che ha impedito all'agente di merge l'applicazione della modifica. Ad esempio, se l'agente di Merge non è possibile applicare un'operazione di inserimento nel Sottoscrittore a causa di una violazione della chiave primaria, registra un **conflict_type** 6 ("inserimento di download non riuscito") e una **reason_code** di 2627, che è la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] messaggio di errore interno di una violazione della chiave primaria: "violazione del vincolo %ls ' %. * ls'. Impossibile inserire la chiave duplicata nell'oggetto ' %. \*ls'. "|  
|**reason_text**|**nvarchar(720)**|Descrizione dell'errore che può essere sensibile al contesto.|  
|**pubid**|**uniqueidentifier**|Identificatore della pubblicazione.|  
|**MSrepl_create_time**|**datetime**|Ora in cui si è verificato il conflitto.|  
|**origin_datasource_id**|**uniqueidentifier**|Identificatore del database in cui ha avuto origine la modifica in conflitto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
