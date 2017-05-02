---
title: Stored procedure XML di sistema | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system stored procedures [SQL Server], XML
- sp_xml_removedocument
- OPENXML statement, system stored procedures
- sp_xml_preparedocument
- XML [SQL Server], system stored procedures
ms.assetid: e60c7f85-6823-4d28-93d6-b053d08cc830
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c76485cd0e24578930b81c7ec537463f16351196
ms.lasthandoff: 04/11/2017

---
# <a name="xml-system-stored-procedures"></a>Stored procedure XML di sistema
  In SQL Server sono disponibili le stored procedure di sistema seguenti, utilizzate insieme all'istruzione OPENXML:  
  
-   [sp_xml_preparedocument &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql.md)  
  
-   [sp_xml_removedocument &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql.md)  
  
 Per scrivere le query tramite l'istruzione OPENXML, è prima necessario creare una rappresentazione interna del documento XML chiamando la stored procedure **sp_xml_preparedocument**. La stored procedure restituisce un handle per la rappresentazione interna del documento XML. Tale handle viene quindi passato a OPENXML, che restituisce viste di set di righe del documento basate su query XPath. In particolare, vengono restituiti un modello di riga e uno o più modelli di colonna.  
  
> [!NOTE]  
>  L'handle del documento restituito dalla stored procedure **sp_xml_preparedocument** è valido per l'intera durata della sessione.  
  
 È possibile rimuovere la rappresentazione interna del documento XML dalla memoria chiamando la stored procedure di sistema **sp_xml_removedocument** .  
  
## <a name="see-also"></a>Vedere anche  
 [OPENXML &#40;Transact-SQL&#41;](../../t-sql/functions/openxml-transact-sql.md)   
 [OPENXML &#40;SQL Server&#41;](../../relational-databases/xml/openxml-sql-server.md)  
  
  
