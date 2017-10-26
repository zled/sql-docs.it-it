---
title: Attestazioni per il servizio Token Windows (c2WTS) e Reporting Services | Documenti Microsoft
ms.custom: The Claims to Windows Token Service (C2WTS) is used by SharePoint and needs to be configured for Kerberos constrained delegation to work with SQL Server Reporting Services properly.
ms.date: 09/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a9397f427cac18d0c8bfc663f6bd477b0440b8a3
ms.openlocfilehash: 8a478bba3cde66967594d5ef02f867de5b33edd7
ms.contentlocale: it-it
ms.lasthandoff: 09/15/2017

---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Attestazioni per il servizio token Windows (C2WTS) e Reporting Services

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Il componente attestazioni per il servizio Token Windows (C2WTS) è necessario se si desidera visualizzare i report in modalità nativa all'interno di [web part di Visualizzatore Report di SQL Server Reporting Services](../report-server-sharepoint/deploy-report-viewer-web-part.md).

C2WTS è necessario installare SQL Server Reporting Services in modalità SharePoint anche se si desidera utilizzare l'autenticazione di Windows per origini dati all'esterno della farm di SharePoint. Il servizio C2WTS è necessario anche se l'origine dati si trova nello stesso computer del servizio condiviso, sebbene in questo scenario la delega vincolata non sia richiesta.

> [!NOTE]
> Integrazione con SharePoint di Reporting Services non è più disponibile dopo SQL Server 2016.

## <a name="report-viewer-web-part-configuration"></a>Configurazione della parte web Visualizzatore report

La web part Visualizzatore Report può essere utilizzata per incorporare report in modalità nativa SQL Server Reporting Services all'interno del sito di SharePoint. Questa web part è disponibile per SharePoint 2013 e SharePoint 2016. Sia SharePoint 2013 e SharePoint 2016 rendono l'utilizzo dell'autenticazione delle attestazioni. Per impostazione predefinita, SQL Server Reporting Services (modalità nativa) utilizza l'autenticazione di Windows. Di conseguenza, C2WTS deve essere configurato correttamente per eseguire correttamente il rendering dei report.

## <a name="sharepoint-mode-integaration"></a>Integaration modalità SharePoint

**In questa sezione si applica solo a SQL Server 2016 Reporting Services e versioni precedenti.**

Il componente attestazioni per il servizio Token Windows (C2WTS) è necessario con la modalità SharePoint di SQL Server Reporting Services se si desidera utilizzare l'autenticazione di Windows per origini dati all'esterno della farm di SharePoint. Questo vale anche se l'utente accede alla origini dati con l'autenticazione di Windows perché la comunicazione tra il front-end web (WFE) e il servizio condiviso Reporting Services sarà sempre l'autenticazione delle attestazioni.

## <a name="steps-needed-to-configure-c2wts"></a>Passaggi necessari per configurare c2WTS

I token creati da C2WTS funzioneranno solo con delega vincolata (vincoli a servizi specifici) e l'opzione di configurazione "Utilizza un qualsiasi protocollo di autenticazione". Come notato in precedenza, se le origini dati si trovano nello stesso computer del servizio condiviso, la delega vincolata non è necessaria.

Se l'ambiente utilizzerà la delega vincolata Kerberos, le origini dati esterne e il servizio SharePoint Server devono trovarsi nello stesso dominio Windows. Qualsiasi servizio basato su Attestazioni per il servizio token Windows (c2WTS) deve usare la delega **vincolata** Kerberos per consentire a c2WTS di usare la transizione del protocollo Kerberos per convertire le attestazioni in credenziali di Windows. Questi requisiti sono validi per tutti i servizi condivisi SharePoint. Per altre informazioni, vedere [Pianificare l'autenticazione Kerberos in SharePoint 2013](http://technet.microsoft.com/library/ee806870.aspx).  

1. Configurare l'account del servizio C2WTS. Aggiungere l'account del servizio al gruppo Administrators locale su ciascun server verrà utilizzato C2WTS.

    Per il **web part Visualizzatore Report**, questo sarà il server Web front-End (WFE). Per **la modalità integrata SharePoint**, questo sarà il server applicazioni in cui è in esecuzione il servizio Reporting Services.

2. Configurare la delega per l'account del servizio C2WTS.

    L'account necessita della delega vincolata con transizione di protocollo e le autorizzazioni per la delega ai servizi che è necessario per comunicare con (ad esempio SQL Server Database Engine, SQL Server Analysis Services). Per configurare la delega è possibile utilizzare lo snap-in utenti e Computer e dovrà essere un amministratore di dominio.

    > [!IMPORTANT]
    > Impostazioni configurare per l'account del servizio C2WTS nella scheda delega deve corrispondere all'account del servizio principali in uso. Per il **web part Visualizzatore Report**, questo sarà l'account del servizio per l'applicazione web di SharePoint. Per **la modalità integrata SharePoint**, questo sarà l'account di servizio Reporting Services.
    >
    > Ad esempio, se si consente l'account del servizio C2WTS delegare a un servizio di SQL, è necessario eseguire la stessa operazione sull'account di servizio Reporting Services per la modalità integrata SharePoint.

    * Fare clic con il pulsante destro del mouse su ogni account del servizio e aprire la finestra di dialogo delle proprietà. Nella finestra di dialogo fare clic sulla scheda **Delega** .

        La scheda delega è visibile solo se l'oggetto ha un nome di entità servizio (SPN) assegnato. C2WTS non richieda un nome SPN per l'Account C2WTS, tuttavia, senza un nome SPN, il **delega** scheda non sarà visibile. Un modo alternativo per configurare la delega vincolata consiste nell'impiego di un'utilità, ad esempio **ADSIEdit**.

    * Di seguito vengono indicate le opzioni di configurazione principali nella scheda relativa alla delega:

        * Selezionare **utente attendibile per la delega solo ai servizi specificati**
        * Selezionare **utilizza un qualsiasi protocollo di autenticazione**

    * Selezionare **Aggiungi** per aggiungere un servizio per la delega.

    * Selezionare **utenti o computer...** * e immettere l'account che ospita il servizio. Ad esempio, se SQL Server è in esecuzione con un account denominato *sqlservice*, immettere `sqlservice`. 

    * Selezionare l'elenco del servizio. Verranno visualizzati i nomi SPN disponibili per tale account. Se non viene visualizzato, il servizio indicato per l'account può essere mancante o inserito in un altro account. è possibile usare l'utilità SetSPN per modificare i nomi SPN.

    * Selezionare OK per uscire dalle finestre di dialogo.

3. Configurare C2WTS *i chiamanti consentiti per*.

    C2WTS è necessario che l'identità 'chiamanti' in modo esplicito elencati nel file di configurazione, **c2wtshost.exe**. C2WTS non accetta richieste da tutti gli utenti autenticati nel sistema, a meno che venga non venga configurato appositamente. In questo caso il "chiamante" è il gruppo di Windows WSS_WPG. Il file c2wtshost.exe. config viene salvato nel percorso seguente:

    Modificando l'account del servizio in Amministrazione centrale SharePoint, per il servizio C2WTS, tale account verrà aggiunto al gruppo WSS_WPG.

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

4. Avviare attestazioni per il servizio Token Windows tramite Amministrazione centrale SharePoint nel **Gestisci servizi nel Server** pagina. Il servizio deve essere avviato nel server che eseguirà l'azione. Ad esempio se si dispone di un server che è un front-end Web e un altro server che è un Server applicazioni con il servizio condiviso SQL Server Reporting Services in esecuzione, è solo necessario avviare C2WTS nel Server applicazioni. C2WTS è necessario in un server front-end Web solo se si esegue la web part Visualizzatore Report.

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
