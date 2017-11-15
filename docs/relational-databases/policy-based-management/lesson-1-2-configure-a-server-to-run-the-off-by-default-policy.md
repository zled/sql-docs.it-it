---
title: Configurare un server per l'esecuzione di criteri Disattivata per impostazione predefinita | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-query-tuning
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: 41c3022d-ab13-443e-ac64-ba1d64584f79
caps.latest.revision: "23"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ebc24ef97d0dc3bce65b4f9e9e0dd419d7ffa524
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="lesson-1-2---configure-a-server-to-run-the-off-by-default-policy"></a>Lezione 1-2: Configurare un server per l'esecuzione di criteri Disattivata per impostazione predefinita
Sono stati creati criteri denominati Disattivata per impostazione predefinita. In questa attività si verificherà se il server è conforme ai requisiti di tali criteri.  
  
### <a name="to-run-the-off-by-default-policy"></a>Per eseguire i criteri Disattivata per impostazione predefinita  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], scegliere **Criteri** e fare clic su **Valuta**.  
  
2.  Nella finestra di dialogo **Valuta criteri[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è possibile selezionare criteri da un'altra istanza di**  o da un file. Per questo passaggio, lasciare l'opzione **Origine[!INCLUDE[ssDE](../../includes/ssde-md.md)] impostata sull'istanza del** .  
  
3.  Nella sezione **Criteri** selezionare i criteri **Off By Default** (Disattivata per impostazione predefinita).  
  
4.  Per determinare se il server è conforme ai criteri, fare clic su **Valuta**.  
  
5.  Nell'area **Risultati[!INCLUDE[ssDE](../../includes/ssde-md.md)] verrà visualizzato un cerchio verde con un segno di spunta se il**  è conforme ai criteri. Verrà visualizzato un cerchio rosso con una X se il [!INCLUDE[ssDE](../../includes/ssde-md.md)] non è conforme ai criteri.  
  
6.  Se si verifica un errore, nell'area **Dettagli di destinazione** verranno visualizzate informazioni aggiuntive nella colonna **Messaggio** . Nella colonna **Messaggio** fare clic su **Visualizza** per visualizzare un report contenente i risultati della verifica per ogni proprietà facet controllata.  
  
7.  La descrizione dei criteri viene visualizzata nella parte inferiore della pagina. Nella sezione **Guida aggiuntiva** è incluso il collegamento ipertestuale configurato per i criteri. Fare clic sul collegamento ipertestuale del messaggio per aprire la pagina Web specificata quando sono stati creat i criteri.  
  
8.  Chiudere il browser e la finestra di dialogo **Visualizzazione dettagliata risultati** .  
  
9. Se il server non è conforme e si vuole disabilitare Posta elettronica database, fare clic su **Applica** nella pagina **Risultati valutazione** .  
  
10. Chiudere le due finestre di dialogo **Visualizzazione dettagliata risultati** e **Valuta criteri** .  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 2: Creazione e applicazione di criteri per gli standard di denominazione](../../relational-databases/policy-based-management/lesson-2-create-and-apply-a-naming-standards-policy.md)  
  
  
  
