---
title: 'Esercitazione: Uso del servizio di archiviazione BLOB di Azure con SQL Server 2016 | Microsoft Docs'
ms.custom:
- SQL2016_New_Updated
ms.date: 01/07/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
caps.latest.revision: 23
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4ae1e9aef727303d55c79463d822c4f62d3cdae0
ms.lasthandoff: 04/11/2017

---
# <a name="tutorial-use-azure-blob-storage-service-with-sql-server-2016"></a>Esercitazione: Uso del servizio di archiviazione BLOB di Azure con SQL Server 2016
Benvenuti nell'esercitazione sull'uso di SQL Server 2016 nel servizio di archiviazione BLOB di Microsoft Azure. Questa esercitazione descrive come usare il servizio di archiviazione BLOB di Microsoft Azure per i file di dati e i backup di SQL Server.  
  
Il supporto di integrazione di SQL Server per il servizio di archiviazione BLOB di Microsoft Azure è stato per la prima volta incluso come funzionalità avanzata di SQL Server 2012 Service Pack 1 CU2, ulteriormente potenziato in SQL Server 2014 e SQL Server 2016. Per una panoramica della funzionalità e dei vantaggi offerti dall'uso di questa funzionalità, vedere [File di dati di SQL Server in Microsoft Azure](../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md). Per una dimostrazione dal vivo, vedere la [demo del ripristino temporizzato](https://channel9.msdn.com/Blogs/Windows-Azure/File-Snapshot-Backups-Demo).  
  
  
**Scarica**<br /><br />**>>**  Per scaricare [!INCLUDE[ssSQL15](../includes/sssql15-md.md)], passare alla pagina  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**.<br /><br />**>>**  Se si ha un account di Azure,  fare clic **[qui](https://azure.microsoft.com/en-us/services/virtual-machines/sql-server/)** per creare rapidamente una macchina virtuale in cui è già installato [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] .  
  
## <a name="what-you-will-learn"></a>Lezioni dell'esercitazione  
Nell'esercitazione viene illustrato come usare i file di dati di SQL Server nel servizio di archiviazione BLOB di Microsoft Azure in più lezioni. Ogni lezione è incentrata su un'attività specifica e le lezioni devono essere completate in sequenza. In primo luogo, si apprenderà come creare un nuovo contenitore nell'archiviazione BLOB con criteri di accesso archiviati e una firma di accesso condiviso. Successivamente, verrà illustrato come creare le credenziali di SQL Server per poter integrare SQL Server con il servizio di archiviazione BLOB di Azure. Verrà quindi eseguito il backup di un database nel servizio di archiviazione BLOB e ne verrà eseguito il ripristino in una macchina virtuale di Azure. Verrà quindi usato il backup del log delle transazioni di snapshot di file di SQL Server 2016 per il ripristino temporizzato e in un nuovo database. Infine, l'esercitazione descriverà l'uso di stored procedure e funzioni di sistema dei metadati per consentire di comprendere e usare i backup di snapshot di file.  
  
In questo articolo si presuppone quanto segue:  
  
-   Viene usata un'istanza locale di SQL Server 2016 con una copia di AdventureWorks2014 installata.  
  
-   Si dispone di un account di archiviazione Azure.  
  
-   Si dispone di almeno una macchina virtuale di Azure con SQL Server 2016 installato e configurata in base a quanto descritto in [Effettuare il provisioning di una macchina virtuale di SQL Server nel portale di Azure](https://azure.microsoft.com/en-us/documentation/articles/virtual-machines-provision-sql-server/). È anche possibile usare una seconda macchina virtuale per lo scenario della [Lezione 8: Ripristinare come nuovo database da un backup del log](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)).  
  
Questa esercitazione è suddivisa in nove lezioni che devono essere completate nell'ordine:  
  
**[Lezione 1: Creare criteri di accesso archiviati e una firma di accesso condiviso in un contenitore di Azure](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)**  
In questa lezione vengono creati i criteri in un nuovo contenitore BLOB e viene generata una firma di accesso condiviso da usare per la creazione delle credenziali di SQL Server.  
  
**[Lezione 2: Creare credenziali di SQL Server usando una firma di accesso condiviso](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**  
In questa lezione vengono create le credenziali usando una chiave di firma di accesso condiviso per archiviare le informazioni di sicurezza usate per accedere all'account di archiviazione di Microsoft Azure.  
  
**[Lezione 3: Backup del database su URL](../relational-databases/lesson-3-database-backup-to-url.md)**  
In questa lezione viene eseguito il backup di un database locale nel servizio di archiviazione BLOB di Microsoft Azure.  
  
**[Lezione 4: Ripristinare il database in una macchina virtuale da un URL](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**  
In questa lezione viene ripristinato un database in una macchina virtuale di Azure dall'archiviazione BLOB di Microsoft Azure.  
  
**[Lezione 5: Eseguire il backup del database con il backup di snapshot di file](../relational-databases/lesson-5-backup-database-using-file-snapshot-backup.md)**  
In questa lezione viene eseguito il backup di un database usando il backup di snapshot di file e i metadati dello snapshot di file di visualizzazione.  
  
**[Lezione 6: Generare attività e backup del log usando il backup di snapshot di file](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**  
In questa lezione viene generata attività nel database e vengono eseguiti diversi backup del log usando il backup di snapshot di file e i metadati dello snapshot di file di visualizzazione.  
  
**[Lezione 7: Eseguire il ripristino temporizzato di un database](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**  
In questa lezione viene eseguito il ripristino temporizzato di un database usando due backup del log di snapshot di file.  
  
**[Lezione 8. Ripristinare come nuovo database dal backup del log](../relational-databases/lesson-8-restore-as-new-database-from-log-backup.md)**  
In questa lezione viene eseguito il ripristino da un backup del log di snapshot di file in un nuovo database in un'altra macchina virtuale.  
  
**[Lezione 9: Gestire set di backup e backup di snapshot di file](../relational-databases/lesson-9-manage-backup-sets-and-file-snapshot-backups.md)**  
In questa lezione vengono eliminati i set di backup non necessari e viene descritto come eliminare i backup di snapshot di file isolati.  
  
## <a name="did-this-article-help-you-were-listening"></a>Questo articolo è stato utile? Commenti e suggerimenti  
Quali informazioni si stanno cercando? La ricerca ha restituito i risultati desiderati? Microsoft incoraggia gli utenti a inviare i propri commenti per migliorare i contenuti Inviare eventuali commenti all'indirizzo [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Tutorial:%20Using%20the%20Microsoft%20Azure%20Blob%20storage%20service%20with%20SQL%20Server%202016%20databases%20page)  
  
## <a name="see-also"></a>Vedere anche  
[File di dati di SQL Server in Microsoft Azure](../relational-databases/databases/sql-server-data-files-in-microsoft-azure.md)  
[Backup di snapshot di file per i file di database in Azure](../relational-databases/backup-restore/file-snapshot-backups-for-database-files-in-azure.md)  
[Backup di SQL Server nell'URL](../relational-databases/backup-restore/sql-server-backup-to-url.md)  
  
  
  


