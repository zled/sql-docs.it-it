---
title: Visualizzare o modificare i percorsi predefiniti per i file di dati e di log | Microsoft Docs
ms.custom: 
ms.date: 06/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- log files [SQL Server], changing default location
- data files [SQL Server], changing default location
ms.assetid: 70a57fda-fcfe-490f-9cf6-5df620e32b2a
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: e1afb149a8b3348660e4e21c879598436eaaedfa
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="view-or-change-the-default-locations-for-data-and-log-files"></a>Visualizzare o modificare i percorsi predefiniti per i file di dati e di log
  
 La procedura consigliata per la protezione dei file di dati e di log consiste nel verificare che siano protetti da elenchi di controllo di accesso (ACL). Impostare gli elenchi di controllo di accesso a livello della radice in cui vengono creati i file.  
 
  
## <a name="view-or-change-the-default-locations-for-database-files"></a>Visualizzare o modificare i percorsi predefiniti per i file di database  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse sul server e scegliere **Proprietà**.  
  
2.  Nel riquadro sinistro della pagina Proprietà fare clic sulla scheda **Impostazioni database** .  
  
3.  Nel pannello **Percorsi predefiniti database**è possibile visualizzare i percorsi predefiniti correnti per i nuovi file di dati e di log. Per modificare un percorso predefinito, immettere un nuovo percorso predefinito nel campo **Dati** o **Log** oppure fare clic sul pulsante Sfoglia per individuare e selezionare un percorso.  
  
>**NOTA:** dopo aver modificato i percorsi predefiniti, è necessario arrestare e avviare il servizio SQL Server per completare la modifica.  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [Creare un database](../../relational-databases/databases/create-a-database.md)  
  
  
