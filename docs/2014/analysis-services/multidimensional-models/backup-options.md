---
title: Opzioni di backup | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [Analysis Services]
- databases [Analysis Services], backing up
ms.assetid: 02d33fc9-f3f4-4b85-8b90-449b68625cf7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 119b06da83da044f2ab8663433f76312540c72a8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141751"
---
# <a name="backup-options"></a>Opzioni di backup
  È possibile eseguire il backup dei database di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in molti modi e in tutti i casi è necessario disporre delle autorizzazioni di amministratore del server e del database. È possibile visualizzare la finestra di dialogo **Backup** di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], selezionare le opzioni di configurazione appropriate e quindi eseguire il backup dalla finestra di dialogo. In alternativa, è possibile creare uno script utilizzando le impostazioni già specificate nel file. Sarà quindi possibile salvare lo script ed eseguirlo quando necessario.  
  
## <a name="backup-and-synchronize"></a>Backup e sincronizzazione  
 Se il database si trova in un'istanza remota di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], è possibile usare la caratteristica di sincronizzazione per eseguire il backup del database nell'istanza locale. In questo modo, è possibile spostare le build di sviluppo di un database nell'ambiente di produzione. Per spostare la build di sviluppo nell'ambiente di produzione, è inoltre possibile utilizzare le procedure tradizionali di backup e ripristino basate su file, ma la sincronizzazione offre funzionalità aggiuntive. Il computer di sviluppo e quello di produzione potrebbero, ad esempio, avere impostazioni di sicurezza diverse. Tramite la sincronizzazione è possibile mantenere tali impostazioni e sincronizzare tutti gli oggetti a esclusione dei ruoli. La sincronizzazione, inoltre, comporta in genere un aggiornamento incrementale degli oggetti che sono diversi nei computer di origine e in quelli di destinazione. Questo tipo di backup incrementale non è disponibile quando si utilizza la caratteristica di backup e ripristino. Per altre informazioni, vedere [Sincronizzare database di Analysis Services](synchronize-analysis-services-databases.md).  
  
> [!IMPORTANT]  
>  L'account del servizio Analysis Services deve disporre delle autorizzazioni per scrivere nel percorso di backup specificato per ogni file. L'utente deve inoltre avere uno dei ruoli seguenti: ruolo di amministratore per l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] o membro di un ruolo del database con autorizzazioni Controllo completo (amministratore) per il database di cui eseguire il backup.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il backup del Database, finestra di dialogo &#40;Analysis Services - dati multidimensionali&#41;](../backup-database-dialog-box-analysis-services-multidimensional-data.md)   
 [Backup e ripristino di database di Analysis Services](backup-and-restore-of-analysis-services-databases.md)   
 [Elemento di backup &#40;XMLA&#41;](../xmla/xml-elements-commands/backup-element-xmla.md)   
 [Il backup, ripristino e sincronizzazione dei database &#40;XMLA&#41;](../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
