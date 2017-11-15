---
title: Oggetti di automazione OLE in Transact-SQL | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-ole
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- triggers [SQL Server], OLE Automation
- batches [SQL Server], OLE Automation
- OLE Automation [SQL Server]
- OLE Automation [SQL Server], about OLE Automation
ms.assetid: a887d956-4cd0-400a-aa96-00d7abd7c44b
caps.latest.revision: "24"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d7946a30f2d87cbbee4dd1f71e7fac192469052f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="ole-automation-objects-in-transact-sql"></a>Oggetti di automazione OLE in Transact-SQL
  [!INCLUDE[tsql](../../includes/tsql-md.md)] include varie stored procedure di sistema che consentono di fare riferimento agli oggetti di automazione OLE in batch, stored procedure e trigger [!INCLUDE[tsql](../../includes/tsql-md.md)] . Queste stored procedure di sistema vengono eseguite come stored procedure estese e gli oggetti di automazione OLE eseguiti tramite tali stored procedure vengono eseguiti nello spazio degli indirizzi di un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] esattamente come le stored procedure estese.  
  
 Le stored procedure di automazione OLE consentono di fare riferimento in batch [!INCLUDE[tsql](../../includes/tsql-md.md)] a oggetti SQL-DMO e a oggetti di automazione OLE personalizzati, ad esempio gli oggetti che espongono l'interfaccia **IDispatch** . Un server OLE in-process personalizzato creato in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] deve includere un gestore degli errori, specificato con l'istruzione **On Error GoTo** , per le subroutine **Class_Initialize** e **Class_Terminate** . Gli errori non gestiti nelle subroutine **Class_Initialize** e **Class_Terminate** possono provocare errori imprevedibili, ad esempio una violazione dell'accesso in un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. È consigliabile disporre inoltre dei gestori degli errori per altre subroutine.  
  
 Per usare un oggetto di automazione OLE in [!INCLUDE[tsql](../../includes/tsql-md.md)] , prima di tutto è necessario chiamare la stored procedure di sistema **sp_OACreate** per creare un'istanza dell'oggetto nello spazio degli indirizzi del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 Richiamare quindi le stored procedure seguenti per utilizzare le proprietà, i metodi e le informazioni sugli errori dell'oggetto:  
  
-   **sp_OAGetProperty** recupera il valore di una proprietà.  
  
-   **sp_OASetProperty** imposta il valore di una proprietà.  
  
-   **sp_OAMethod** chiama un metodo.  
  
-   **sp_OAGetErrorInfo** recupera informazioni sugli errori più recenti.  
  
 Quando l'oggetto non è più necessario, chiamare **sp_OADestroy** per deallocare l'istanza dell'oggetto creata con **sp_OACreate**.  
  
 Gli oggetti di automazione OLE restituiscono dati tramite valori e metodi di proprietà. **sp_OAGetProperty** e **sp_OAMethod** restituiscono questi valori dei dati sotto forma di set di risultati.  
  
 L'ambito di un oggetto di automazione OLE è il batch. Tutti i riferimenti all'oggetto devono essere inclusi in un unico batch, stored procedure o trigger.  
  
 Gli oggetti di automazione OLE di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supportano l'attraversamento dell'oggetto a cui fanno riferimento per accedere agli altri oggetti che contiene. Se, ad esempio, si usa l'oggetto SQL-DMO di **SQLServer** , è possibile fare riferimento ai database e alle tabelle disponibili in tale server.  
  
## <a name="related-content"></a>Contenuto correlato  
 [Sintassi della gerarchia degli oggetti &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/object-hierarchy-syntax-transact-sql.md)  
  
 [Configurazione superficie di attacco](../../relational-databases/security/surface-area-configuration.md)  
  
 [Opzione di configurazione del server Ole Automation Procedures](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
 [sp_OACreate &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-oacreate-transact-sql.md)  
  
 [sp_OAGetProperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-oagetproperty-transact-sql.md)  
  
 [sp_OASetProperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-oasetproperty-transact-sql.md)  
  
 [sp_OAMethod &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-oamethod-transact-sql.md)  
  
 [sp_OAGetErrorInfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-oageterrorinfo-transact-sql.md)  
  
 [sp_OADestroy &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-oadestroy-transact-sql.md)  
  
  
