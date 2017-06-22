---
title: Attestazioni per il servizio Token Windows (c2WTS) e Reporting Services | Documenti Microsoft
ms.custom: 
ms.date: 06/12/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- c2wts.exe.config
- SharePoint mode
- C2WTS
- WSS_WPG
ms.assetid: 4d380509-deed-4b4b-a9c1-a9134cc40641
caps.latest.revision: 17
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2ab5f4b5d2774d9dc944ad17bb55063388b70a6d
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Attestazioni per il servizio token Windows (c2WTS) e Reporting Services

[!INCLUDE[ssrs-appliesto-sql2016-xpreview](../../includes/ssrs-appliesto-sql2016-xpreview.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

  Il componente Attestazioni per il servizio token Windows (c2WTS) di SharePoint è necessario con la modalità SharePoint di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] se si vuole usare l'autenticazione di Windows per le origini dati all'esterno della farm di SharePoint. Questo vale anche se l'utente accede alla origini dati con l'autenticazione di Windows perché la comunicazione tra il front-end Web e il servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] condiviso sarà sempre un'autenticazione delle attestazioni.  
  
 Il servizio c2WTS è necessario anche se l'origine dati si trova nello stesso computer del servizio condiviso, sebbene in questo scenario la delega vincolata non sia richiesta.  
  
 I token creati da c2WTS funzioneranno solo con la delega vincolata (vincoli a servizi specifici) e l'opzione di configurazione che prevede l'uso di qualsiasi protocollo di autenticazione. Come notato in precedenza, se le origini dati si trovano nello stesso computer del servizio condiviso, la delega vincolata non è necessaria.  
  
 Se l'ambiente utilizzerà la delega vincolata Kerberos, le origini dati esterne e il servizio SharePoint Server devono trovarsi nello stesso dominio Windows. Qualsiasi servizio basato su Attestazioni per il servizio token Windows (c2WTS) deve usare la delega **vincolata** Kerberos per consentire a c2WTS di usare la transizione del protocollo Kerberos per convertire le attestazioni in credenziali di Windows. Questi requisiti sono validi per tutti i servizi condivisi SharePoint. Per altre informazioni, vedere [Pianificare l'autenticazione Kerberos in SharePoint 2013](http://technet.microsoft.com/library/ee806870.aspx).  
  
 La procedura viene riepilogata in questo argomento.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
>  Nota: alcuni passaggi della configurazione possono variare o potrebbero non funzionare in determinate topologie farm. Un'installazione in un server singolo, ad esempio, non supporta i servizi c2WTS di Windows Identity Foundation e di conseguenza gli scenari di delega di attestazioni per il servizio token Windows non sono possibili con questa configurazione della farm.

> [!IMPORTANT]
> Se si usa Power View per gestire le cartelle di lavoro di Power Pivot, è necessario apportare modifiche alla configurazione di [Office Online Server](https://technet.microsoft.com/library/jj219437\(v=office.16\).aspx). Per altre informazioni, vedere i white paper seguenti. 
>
> - [Distribuzione di SQL Server 2016 Power Pivot e Power View in SharePoint 2016](../../analysis-services/instances/install-windows/deploying-sql-server-2016-powerpivot-and-power-view-in-sharepoint-2016.md)
> 
> - [Distribuzione di SQL Server 2016 PowerPivot e Power View in una farm di SharePoint 2016 a più livelli](../../analysis-services/instances/install-windows/deploy-powerpivot-and-power-view-multi-tier-sharepoint-2016-farm.md)
  
### <a name="basic-steps-needed-to-configure-c2wts"></a>Passaggi di base necessari per configurare c2WTS  
  
1.  Configurare l'account del servizio c2WTS. Aggiungere l'account del servizio al gruppo Administrators locale in ogni server applicazioni in che esegue c2WTS. Verificare anche che l'account abbia i seguenti diritti sui criteri di sicurezza locali:  
  
    -   Agisci come parte del sistema operativo  
  
    -   Rappresenta un client dopo l'autenticazione  
  
    -   Accedi come servizio  
  
2.  Configurare la delega per l'account del servizio c2WTS. L'account necessita della delega vincolata con transizione di protocollo e delle autorizzazioni per la delega ai servizi con cui deve comunicare, ovvero il motore di SQL Server e SQL Server Analysis Services. Per configurare la delega, è possibile usare lo snap-in Utenti e computer di Active Directory.  

    > [!IMPORTANT]
    > Qualsiasi impostazione configurata per l'account del servizio C2WTS nella scheda relativa alla delega deve corrispondere all'account del servizio Reporting Services. Ad esempio, se si consente all'account del servizio C2WTS la delega a un servizio SQL, è necessario eseguire la stessa operazione per l'account del servizio Reporting Services.
  
    1.  Fare clic con il pulsante destro del mouse su ogni account del servizio e aprire la finestra di dialogo delle proprietà. Nella finestra di dialogo fare clic sulla scheda **Delega** .  
  
        > [!NOTE]  
        >  Nota: la scheda relativa alla delega è visibile solo se all'oggetto è assegnato un nome dell'entità servizio (SPN). Sebbene c2WTS non richieda un nome SPN per il proprio account, senza tale nome la scheda **Delega** non sarà visibile. Un modo alternativo per configurare la delega vincolata consiste nell'impiego di un'utilità, ad esempio **ADSIEdit**.  
  
    2.  Di seguito vengono indicate le opzioni di configurazione principali nella scheda relativa alla delega:  
  
        -   Selezionare "Utente attendibile per la delega solo ai servizi specificati"  
  
        -   Selezionare "Utilizza un qualsiasi protocollo di autenticazione"  

    3. Selezionare **Aggiungi** per aggiungere un servizio per la delega.
    
    4. Selezionare **utenti o computer...** * e immettere l'account che ospita il servizio. Ad esempio, se SQL Server è in esecuzione con un account denominato *sqlservice*, immettere `sqlservice`.
    
    5. Selezionare l'elenco del servizio. Verranno visualizzati i nomi SPN disponibili per tale account. Se non viene visualizzato, il servizio indicato per l'account può essere mancante o inserito in un altro account. è possibile usare l'utilità SetSPN per modificare i nomi SPN.
    
    6. Selezionare OK per uscire dalle finestre di dialogo.
  
3.  Configurare i chiamanti consentiti per c2WTS  
  
     In c2WTS è necessario che le identità chiamanti siano elencate esplicitamente nel file di configurazione **c2WTShost.exe.config**. c2WTS non accetta richieste da tutti gli utenti autenticati nel sistema, a meno che venga configurato appositamente. In questo caso il chiamante è il gruppo di Windows WSS_WPG. Il file c2WTShost.exe.config viene salvato nel percorso seguente:  
     
     > [!NOTE]
     > Modificando l'account del servizio in Amministrazione centrale SharePoint, per il servizio C2WTS, tale account verrà aggiunto al gruppo WSS_WPG.
  
     **\Programmi\Windows Identity Foundation\v3.5\c2WTShost.exe.config**  
  
     Di seguito viene illustrato un esempio del file di configurazione:  
  
    ```  
    <configuration>  
      <windowsTokenService>  
        <!--  
            By default no callers are allowed to use the Windows Identity Foundation Claims To NT Token Service.  
            Add the identities you wish to allow below.  
          -->  
        <allowedCallers>  
          <clear/>  
          <add value="WSS_WPG" />  
        </allowedCallers>  
      </windowsTokenService>  
    </configuration>  
    ```    
4.  Avviare Attestazioni per il servizio token Windows di Share Point tramite Amministrazione centrale SharePoint nella pagina **Gestisci servizi nel server** . Il servizio deve essere avviato nel server che eseguirà l'azione. Ad esempio, in presenza di un front-end Web e di un server applicazioni in cui è in esecuzione il servizio [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] condiviso, è sufficiente avviare c2WTS solo sul server applicazioni. c2WTS non è necessario nel front-end Web.

## <a name="next-steps"></a>Passaggi successivi

[Panoramica di Claims to Windows Token Service (C2WTS)](http://msdn.microsoft.com/library/ee517278.aspx)   
[Piano per l'autenticazione Kerberos in SharePoint 2013](http://technet.microsoft.com/library/ee806870.aspx)  

Ulteriori domande? [Provare a porre il forum di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
