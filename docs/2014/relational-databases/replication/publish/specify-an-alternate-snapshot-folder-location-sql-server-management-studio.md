---
title: Specificare un percorso alternativo per la cartella snapshot (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], alternate folder locations
- snapshot replication [SQL Server], alternate folder locations
- alternate snapshot folders [SQL Server replication]
ms.assetid: 9293f0eb-5531-47ec-b6e2-0392823ce5cc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cae9676985ce2858d7eae1e2f6dc139ee6e4ed54
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48132951"
---
# <a name="specify-an-alternate-snapshot-folder-location-sql-server-management-studio"></a>Specifica di un percorso alternativo per la cartella snapshot (SQL Server Management Studio)
  Specificare un percorso alternativo per lo snapshot nella pagina **Snapshot** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**. Per ulteriori informazioni sull'accesso a questa finestra di dialogo, vedere [View and Modify Publication Properties](view-and-modify-publication-properties.md).  
  
### <a name="to-specify-an-alternate-snapshot-location"></a>Per specificare un percorso alternativo per lo snapshot  
  
1.  Nella pagina **Snapshot** della finestra di dialogo **Proprietà pubblicazione - \<Pubblicazione>**:  
  
    1.  Selezionare **Inserisci i file nella cartella seguente**e quindi fare clic su **Sfoglia** per passare a una directory oppure immettere il percorso della directory in cui devono essere archiviati i file di snapshot.  
  
        > [!NOTE]  
        >  L'agente snapshot deve disporre delle autorizzazioni di scrittura per la directory specificata, mentre l'agente di distribuzione o l'agente di merge deve disporre delle autorizzazioni di lettura. Se si usano sottoscrizioni pull, è necessario specificare una directory condivisa come percorso UNC (Universal Naming Convention), ad esempio \\\nomecomputer\snapshot. Per altre informazioni, vedere [Proteggere la cartella snapshot](../security/secure-the-snapshot-folder.md).  
  
    2.  Deselezionare **Inserisci i file nella cartella predefinita** a meno che non sia necessario scrivere i file di snapshot in entrambe le posizioni.  
  
     Per comprimere i file di snapshot, selezionare **Comprimi i file di snapshot in questa cartella**. La compressione viene in genere utilizzata per le connessioni a larghezza di banda ridotta e per i percorsi alternativi per lo snapshot nei supporti rimovibili, ad esempio un CD-ROM.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Posizioni alternative della cartella snapshot](../alternate-snapshot-folder-locations.md)   
 [Configurare le proprietà dello snapshot &#40;programmazione Transact-SQL della replica&#41;](configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Specificare la posizione predefinita degli snapshot &#40;SQL Server Management Studio&#41;](../specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Modificare le proprietà di pubblicazioni e articoli](change-publication-and-article-properties.md)   
 [Inizializzare una sottoscrizione con uno snapshot](../initialize-a-subscription-with-a-snapshot.md)  
  
  
