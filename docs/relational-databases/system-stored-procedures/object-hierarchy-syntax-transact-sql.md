---
title: Oggetto sintassi della gerarchica (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], hierarchy syntax
ms.assetid: 7ed8df86-9fd2-4e09-96bc-5381fec85f65
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 979d67b930d95817c0c27f671885c9b5fd9fb0d4
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43032539"
---
# <a name="object-hierarchy-syntax-transact-sql"></a>Sintassi della gerarchia degli oggetti (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Il *propertyname* parametri di sp_OAGetProperty e sp_OASetProperty e il *NomeMetodo* parametro di sp_OAMethod supportano una sintassi di gerarchia di oggetti che è simile a quella di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. Quando viene adottata questa sintassi speciale, i parametri sopraindicati seguono il seguente formato generale.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
'TraversedObject.PropertyOrMethod'  
```  
  
## <a name="arguments"></a>Argomenti  
 *TraversedObject*  
 È un oggetto OLE della gerarchia sotto il *vengono restituite le* specificato nella stored procedure. Utilizzare la sintassi di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] per specificare una serie di raccolte, proprietà oggetto e metodi che restituiscono oggetti. I vari identificatori di oggetti della serie devono essere separati da un punto (.).  
  
 Un elemento della serie potrebbe essere il nome di una raccolta. Per specificare una raccolta, utilizzare la seguente sintassi:  
  
 Raccolta ("*elemento*")  
  
 Le virgolette doppie (") sono obbligatorie. La sintassi di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] con il punto esclamativo (!) non è supportata per le raccolte.  
  
 *Non*  
 È il nome di una proprietà o metodo per la *TraversedObject*.  
  
 Per specificare tutti i parametri indice o metodo tramite i parametri di sp_OAGetProperty, sp_OASetProperty o sp_OAMethod (compreso il supporto per i parametri di output di sp_OAMethod), utilizzare la sintassi seguente:  
  
 *Non*  
  
 Per specificare tutti i parametri indice o metodo tra parentesi e ignorare di conseguenza tutti i parametri indice o metodo di sp_OAGetProperty, sp_OASetProperty o sp_OAMethod, utilizzare la sintassi seguente:  
  
 *PropertyOrMethod*([ *ParameterName*: =] "*parametro*" [,...])  
  
 Le virgolette doppie (") sono obbligatorie. Tutti i parametri denominati devono essere specificati dopo tutti i parametri posizionali.  
  
## <a name="remarks"></a>Note  
 Se *TraversedObject* non viene specificato, *PropertyOrMethod* è obbligatorio.  
  
 Se *PropertyOrMethod* non viene specificato, il *TraversedObject* viene restituito come un parametro di output di token di oggetto da procedure di automazione OLE archiviati. Se *PropertyOrMethod* è specificato, la proprietà o metodo di *TraversedObject* viene chiamato, e il valore della proprietà o valore restituito del metodo viene restituito come parametro di output dell'automazione OLE stored procedure.  
  
 Se un elemento di *TraversedObject* elenco non restituisce un oggetto OLE, viene generato un errore.  
  
 Per ulteriori informazioni sulla sintassi degli oggetti OLE di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], consultare la documentazione di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].  
  
 Per altre informazioni sui codici restituiti HRESULT, vedere [sp_OACreate &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-oacreate-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
 Di seguito sono esempi di sintassi della gerarchia degli oggetti che usano un oggetto SQL-DMO di SQL Server.  
  
```  
-- Get the AdventureWorks2012 Person.Address Table object.  
EXEC @hr = sp_OAGetProperty @object,  
   'Databases("AdventureWorks2012").Tables("Person.Address")',  
   @table OUT  
  
-- Get the Rows property of the AdventureWorks2012 Person.Address table.  
EXEC @hr = sp_OAGetProperty @object,  
   'Databases("AdventureWorks2012").Tables("Person.Address").Rows',  
   @rows OUT  
  
-- Call the CheckTable method to validate the   
-- AdventureWorks2012 Person.Address table.  
EXEC @hr = sp_OAMethod @object,  
   'Databases("AdventureWorks2012").Tables("Person.Address").CheckTable',  
   @checkoutput OUT  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Script di esempio di automazione OLE](../../relational-databases/stored-procedures/ole-automation-sample-script.md)   
 [Stored procedure di automazione &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)  
  
  
