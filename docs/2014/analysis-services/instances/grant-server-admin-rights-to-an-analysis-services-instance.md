---
title: Concedere autorizzazioni di amministratore del Server (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- administrator rights [Analysis Services]
- server-wide administrative permissions [Analysis Services]
ms.assetid: 20d1234b-a457-4a84-ae08-fe356870c466
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4b3100fc8ccf9f21a6c0cf760d799dcf1b15cbb5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48202211"
---
# <a name="grant-server-administrator-permissions-analysis-services"></a>Concedere autorizzazioni amministrative per il server (Analysis Services)
  I membri del ruolo di amministratore del server in un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dispongono di accesso illimitato a tutti gli oggetti e i dati di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in tale istanza. Per effettuare un'attività a livello di intero server, ad esempio la creazione o l'elaborazione di un database, la modifica delle proprietà del server o l'avvio di una traccia, per finalità diverse dall'elaborazione degli eventi, un utente deve essere membro del ruolo di amministratore del server.  
  
 L'appartenenza al ruolo viene stabilita quando viene installato [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . L'utente che esegue il programma di installazione può aggiungersi al ruolo o aggiungere un altro utente, in caso di esecuzione del provisioning del server. L'appartenenza al ruolo può essere modificata dopo l'installazione utilizzando la procedura riportata di seguito.  
  
## <a name="modify-server-role-membership"></a>Modificare l'appartenenze al ruolo del server  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], fare clic con il pulsante destro del mouse sul nome dell'istanza in Esplora oggetti e quindi scegliere **Proprietà**.  
  
2.  Fare clic sulla scheda **Sicurezza** nel riquadro **Selezione pagina** , quindi selezionare **Aggiungi** nella parte inferiore della pagina per aggiungere uno o più utenti o gruppi di Windows al ruolo del server.  
  
     ![Finestra di dialogo Aggiungi utenti management Studio](../media/ssas-serveradminadd.png "finestra di dialogo Aggiungi utenti management Studio")  
  
 Durante la fase di installazione di SQL Server viene richiesto di specificare almeno un account utente come amministratore di sistema di Analysis Services.  
  
 Per impostazione predefinita, ai membri del gruppo di amministratori locali vengono anche garantiti diritti amministrativi in Analysis Services. Sebbene al gruppo locale non venga garantita esplicitamente l'appartenenza al ruolo di amministratore del server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , gli amministratori locali possono creare database, aggiungere utenti e autorizzazioni ed effettuare qualsiasi altra attività consentita agli amministratori di sistema. Questo comportamento è configurabile, Infatti è determinato dal `BuiltinAdminsAreServerAdmins` proprietà del server, che è impostata su **true** per impostazione predefinita. Questa proprietà può essere modificata in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per altre informazioni, vedere [Security Properties](../server-properties/security-properties.md).  
  
 È anche possibile gestire i ruoli del server tramite la libreria AMO (Analysis Management Objects). Per altre informazioni, vedere [Sviluppo con AMO &#40;Analysis Management Objects&#41;](../multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Autorizzare l'accesso a oggetti e operazioni &#40;Analysis Services&#41;](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)   
 [I ruoli di sicurezza &#40;Analysis Services - dati multidimensionali&#41;](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
  
