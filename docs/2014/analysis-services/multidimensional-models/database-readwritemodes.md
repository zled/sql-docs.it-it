---
title: Proprietà readwritemode del database | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- databases [Analysis Services], read/write
- databases [Analysis Services], read-only
ms.assetid: 03d7cb5c-7ff0-4e15-bcd2-7075d1b0dd69
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f8a655c379f512f882534166a8c561524e02ce88
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065940"
---
# <a name="database-readwritemodes"></a>Proprietà ReadWriteMode del database
  Spesso, un amministratore di database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] vuole impostare un database di lettura/scrittura in sola lettura o viceversa. Queste situazioni sono il più delle volte determinate da esigenze aziendali, ad esempio la condivisione della stessa cartella di database tra più server per ottenere la scalabilità orizzontale di una soluzione, e per migliorare le prestazioni. In queste situazioni, il `ReadWriteMode` database proprietà permette il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba di modificare facilmente la modalità operativa del database.  
  
## <a name="readwritemode-database-property"></a>Proprietà di database ReadWriteMode  
 La proprietà di database `ReadWriteMode` specifica se il database è in modalità lettura/scrittura o in modalità sola lettura. Questi sono i due soli valori possibili della proprietà. Quando il database è in modalità sola lettura, non è possibile applicare modifiche o aggiornamenti. Quando invece il database è in modalità lettura/scrittura, le modifiche e gli aggiornamenti possono verificarsi. Il `ReadWriteMode` proprietà del database è definita come una proprietà di sola lettura, può essere impostato solo tramite un `Attach` comando.  
  
 Quando un database è in modalità sola lettura, si applicano determinate restrizioni che influiscono sul set ordinario di operazioni consentite sul database. Per informazioni sulle operazioni con restrizioni, vedere la tabella seguente.  
  
|Modalità ReadOnly|Operazioni con restrizioni|  
|-------------------|---------------------------|  
|Comandi XML/A<br /><br /> <br /><br /> Nota: quando si esegue uno di questi comandi, viene generato un errore.|`Create`<br /><br /> `Alter`<br /><br /> `Delete`<br /><br /> `Process`<br /><br /> `MergePartitions`<br /><br /> `DesignAggregations`<br /><br /> `CommitTransaction`<br /><br /> `Restore`<br /><br /> `Synchronize`<br /><br /> `Insert`<br /><br /> `Update`<br /><br /> `Drop`<br /><br /> <br /><br /> Nota: il writeback delle celle è consentito nei database impostati in sola lettura, tuttavia non è possibile eseguire il commit delle modifiche.|  
|Istruzioni MDX<br /><br /> <br /><br /> Nota: quando si esegue una di queste istruzioni, viene generato un errore.|`COMMIT TRAN`<br /><br /> `CREATE SESSION CUBE`<br /><br /> `ALTER CUBE`<br /><br /> `ALTER DIMENSION`<br /><br /> `CREATE DIMENSION MEMBER`<br /><br /> `DROP DIMENSION MEMBER`<br /><br /> `ALTER DIMENSION`<br /><br /> <br /><br /> Nota: Gli utenti di Excel non è possibile utilizzare la caratteristica di raggruppamento nelle tabelle Pivot, perché tale caratteristica viene implementata internamente tramite `CREATE SESSION CUBE` comandi.|  
|Istruzioni DMX<br /><br /> <br /><br /> Nota: quando si esegue una di queste istruzioni, viene generato un errore.|`CREATE [SESSION] MINING STRUCTURE`<br /><br /> `ALTER MINING STRUCTURE`<br /><br /> `DROP MINING STRUCTURE`<br /><br /> `CREATE [SESSION] MINING MODEL`<br /><br /> `DROP MINING MODEL`<br /><br /> `IMPORT`<br /><br /> `SELECT INTO`<br /><br /> `INSERT`<br /><br /> `UPDATE`<br /><br /> `DELETE`|  
|Operazioni in background|Le operazioni in background che comportano la modifica del database sono disabilitate, ad esempio l'elaborazione lenta e la memorizzazione nella cache attiva.|  
  
## <a name="readwritemode-usage"></a>Utilizzo di ReadWriteMode  
 La proprietà di database `ReadWriteMode` deve essere utilizzata come parte di un comando di database `Attach`. Il `Attach` comando consente la proprietà del database essere impostata su `ReadWrite` o `ReadOnly`. Il valore della proprietà di database `ReadWriteMode` non può essere aggiornato direttamente perché la proprietà è definita di sola lettura. I database vengono creati con la proprietà `ReadWriteMode` impostata su `ReadWrite`. Non è possibile creare un database in modalità sola lettura.  
  
 Per cambiare il `ReadWriteMode` proprietà tra database `ReadWrite` e `ReadOnly`, è necessario eseguire una sequenza di `Detach/Attach` comandi.  
  
 Tutte le operazioni di database, ad eccezione di `Attach`, mantenere il `ReadWriteMode` proprietà nello stato corrente del database. Ad esempio, operazioni come `Alter`, `Backup`, `Restore` e `Synchronize` mantengono il valore di `ReadWriteMode`.  
  
> [!NOTE]  
>  È possibile creare cubi locali da un database di sola lettura.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Collegamento e scollegamento di database di Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Spostare un Database di Analysis Services](move-an-analysis-services-database.md)   
 [Elemento Detach](../xmla/xml-elements-commands/detach-element.md)   
 [Elemento Attach](../xmla/xml-elements-commands/attach-element.md)  
  
  