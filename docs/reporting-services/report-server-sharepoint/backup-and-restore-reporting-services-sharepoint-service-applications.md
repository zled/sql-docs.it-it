---
title: Backup e ripristino di applicazioni di servizio SharePoint di Reporting Services | Documenti Microsoft
ms.custom: 
ms.date: 09/25/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: b6dcd64d6f9662ae592474053e6cc9bbce53a83e
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---
# <a name="back-up-and-restore-reporting-services-sharepoint-service-applications"></a>Backup e ripristino di applicazioni di servizio SharePoint di Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

[!INCLUDE [ssrs-previous-versions](../../includes/ssrs-previous-versions.md)]

In questo argomento viene descritto come eseguire il backup e ripristinare un [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] applicazione di servizi tramite Amministrazione centrale SharePoint o PowerShell.

> [!NOTE]
> Integrazione con SharePoint di Reporting Services non è più disponibile dopo SQL Server 2016.

## <a name="before-you-begin"></a>Operazioni preliminari

### <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni

> [!NOTE]
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]applicazioni di servizio possono essere parzialmente backup e ripristino di SharePoint utilizzando backup e ripristino delle funzionalità. **Sono necessari passaggi aggiuntivi** , illustrati in questo argomento. Attualmente il processo di backup **non** eseguire il backup delle chiavi di crittografia e le credenziali per gli account di esecuzione automatica (UEA) o l'autenticazione di windows per il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] database.

### <a name="recommendations"></a>Indicazioni
  
-   Eseguire il backup delle chiavi di crittografia prima di avviare il backup di SharePoint. Se si esegue il backup delle chiavi di crittografia, quindi non sarà in grado di accedere ai dati crittografati dopo il ripristino dell'applicazione di servizio. Sarà necessario eliminare i dati crittografati.  
  
-   Verificare se nell'applicazione di servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] viene utilizzato un account di esecuzione automatica o l'autenticazione di Windows per l'accesso al database. In caso affermativo, verificare quali sono le credenziali appropriate, per poter configurare correttamente l'applicazione di servizio dopo il processo di ripristino.  
  
-   Esaminare il log di backup di SharePoint viene creato nella stessa cartella del file di backup. Il file è in genere denominato **spbackup.log**  
  
## <a name="back-up-the-service-application"></a>Eseguire il backup dell'applicazione di servizio

 Completare i passaggi seguenti nell'ordine indicato:  
  
1.  Eseguire il backup delle chiavi di crittografia  
  
2.  Eseguire il backup dell'applicazione di servizio  
  
3.  Verificare se nell'applicazione di servizio viene utilizzato un account di esecuzione automatica o l'autenticazione di Windows per l'accesso al database. In caso affermativo, annotare le credenziali in modo da poterle utilizzare per configurare l'applicazione di servizio dopo il ripristino.  

### <a name="back-up-the-encryption-keys-using-sharepoint-central-administration"></a>Il backup delle chiavi di crittografia tramite Amministrazione centrale SharePoint

Per informazioni sul backup delle chiavi di crittografia di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vedere la sezione "Chiavi di crittografia" di [Gestire un'applicazione di servizio SharePoint di Reporting Services](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md).  

### <a name="back-up-the-service-application-using-sharepoint-central-administration"></a>Eseguire il backup dell'applicazione di servizio tramite Amministrazione centrale SharePoint

Per eseguire il backup dell'applicazione di servizio, attenersi alla procedura seguente:  
  
1.  In Amministrazione centrale SharePoint scegliere **eseguire un backup** nel **di Backup e ripristino** gruppo.  
  
2.  Nel nodo **Servizi condivisi** espandere **Applicazioni di servizi condivisi** e selezionare l'applicazione di servizio. L'applicazione sarà di tipo **Applicazione di servizio SQL Server Reporting Services**.  
  
3.  Fare clic su **Avanti**.  
  
4.  Digitare il percorso per il **percorso Backup:** e selezionare **avvia Backup**  
  
5.  Ripetere il processo precedente ma, anziché selezionare l'applicazione di servizio, espandere il nodo **Proxy servizi condivisi** e selezionare il proxy dell'applicazione di servizio. Il proxy sarà di tipo **Proxy dell'applicazione di servizio SQL Server Reporting Services**.  
  
 Per ulteriori informazioni, vedere gli argomenti seguenti nella documentazione di SharePoint:  
  
 [Eseguire il backup di un'applicazione di servizio (SharePoint Foundation 2010) nella documentazione di SharePoint](http://msdn.microsoft.com/library/ee748601.aspx).  
  
 [Eseguire il backup di un'applicazione di servizio (SharePoint Server 2010)](http://technet.microsoft.com/library/ee428318.aspx)  
  
### <a name="verify-execution-account-and-database-authentication"></a>Verificare l'autenticazione di database e account di esecuzione

 **Account di esecuzione:** per verificare se nell'applicazione di servizio viene utilizzato un account di esecuzione:  
  
1.  In Amministrazione centrale SharePoint, selezionare **Gestisci applicazioni di servizio** nel **Application Management** gruppo.  
  
2.  Selezionare il nome dell'applicazione di servizio e quindi **Gestisci** nella barra multifunzione di SharePoint.  
  
3.  Selezionare **Account di esecuzione**.  
  
4.  Se è configurato un account di esecuzione, è necessario conoscere le credenziali per ripristinare il backup dell'applicazione di servizio. Non procedere con le operazioni di backup e ripristino fino a quando non si conoscono le credenziali corrette.  
  
 **Autenticazione del database:** per verificare se nell'applicazione di servizio viene utilizzata l'autenticazione di Windows per l'autenticazione del database:  
  
1.  In Amministrazione centrale SharePoint, selezionare **Gestisci applicazioni di servizio** nel **Application Management** gruppo.  
  
2.  Selezionare il nome dell'applicazione di servizio e quindi **proprietà** nella barra multifunzione di SharePoint.  
  
3.  Analizzare la sezione **Database di servizio di SQL Server Reporting Services (SSRS)** .  
  
4.  Se è configurata l'autenticazione di Windows, è necessario conoscere le credenziali per poter configurare l'applicazione di servizio dopo il ripristino. Non procedere con le operazioni di backup e ripristino fino a quando non si conoscono le credenziali corrette.  
  
## <a name="restore-the-service-application"></a>Ripristinare l'applicazione di servizio

 Completare i passaggi seguenti nell'ordine indicato:  
  
1.  Ripristinare l'applicazione di servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
2.  Ripristinare le chiavi di crittografia.  
  
3.  Se nell'applicazione di servizio viene utilizzato un account di esecuzione o l'autenticazione di Windows per l'accesso al database, configurare le credenziali.  
  
### <a name="restore-the-service-application-using-sharepoint-central-administration"></a>Ripristinare l'applicazione di servizio tramite Amministrazione centrale SharePoint
  
1.  In Amministrazione centrale SharePoint scegliere **ripristinare da un backup** nel **di Backup e ripristino** gruppo.  
  
2.  Digitare il percorso del file di backup in **percorso Directory di Backup** e selezionare **aggiornamento**.  
  
3.  Selezionare il backup dell'applicazione di servizio dal **componente principale** elenco e quindi selezionare **Avanti**.  
  
4.  Selezionare il [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dell'applicazione e quindi selezionare **Avanti**.  
  
5.  Nella sezione **Nomi e password di accesso** digitare la password per il nome di accesso. La casella Nome account di accesso deve essere popolata con l'account di accesso utilizzato dall'applicazione di servizio prima la parte posteriore backup.  
  
6.  Selezionare **Avvia ripristino**.  
  
7.  Ripetere il processo precedente ma, anziché ripristinare l'applicazione di servizio, espandere il nodo **Servizi condivisi** , quindi il nodo **Applicazioni di servizi condivisi** .  
  
 Per ulteriori informazioni, vedere gli argomenti seguenti nella documentazione di SharePoint:  
  
 [Ripristinare un'applicazione di servizio (SharePoint Foundation 2010)](http://msdn.microsoft.com/library/ee748615.aspx).  
  
 [Ripristinare un'applicazione di servizio (SharePoint Server 2010)](https://technet.microsoft.com/library/ee428305.aspx).  

### <a name="restore-the-encryption-keys-using-sharepoint-central-administration"></a>Ripristinare le chiavi di crittografia tramite Amministrazione centrale SharePoint

 Per informazioni sul ripristino delle chiavi di crittografia di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , vedere la sezione "Chiavi di crittografia" di [Gestire un'applicazione di servizio SharePoint di Reporting Services](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md).  

### <a name="configure-the-execution-account-and-database-authentication"></a>Configurare l'autenticazione di database e account di esecuzione

 **Account di esecuzione:** se nell'applicazione di servizio viene utilizzato un account di esecuzione, attenersi alla procedura seguente per configurarlo:  
  
1.  In Amministrazione centrale SharePoint, selezionare **Gestisci applicazioni di servizio** nel **Application Management** gruppo.  
  
2.  Selezionare il nome dell'applicazione di servizio e quindi **Gestisci** nella barra multifunzione di SharePoint.  
  
3.  Selezionare **Account di esecuzione**.  
  
4.  Digitare l'account e la password, quindi selezionare la casella **Specifica account di esecuzione** .  
  
5.  Fare clic su **OK**.  
  
 **Autenticazione del database:** se nell'applicazione di servizio viene utilizzata l'autenticazione di Windows per l'autenticazione del database, attenersi alla procedura seguente:  
  
1.  In Amministrazione centrale SharePoint scegliere **Gestisci applicazioni di servizio** nel **Application Management** gruppo.  
  
2.  Selezionare il nome dell'applicazione di servizio e quindi **proprietà** nella barra multifunzione di SharePoint.  
  
3.  Analizzare la sezione **Database di servizio di SQL Server Reporting Services (SSRS)** .  
  
4.  Selezionare **Autenticazione di Windows**.  
  
5.  Digitare l'account e la password. Selezionare **Usa come credenziali di Windows** , se appropriato.  
  
6.  Selezionare **Ok**

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
