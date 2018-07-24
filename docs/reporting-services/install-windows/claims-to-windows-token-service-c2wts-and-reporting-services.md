---
title: Attestazioni per il servizio token Windows (c2WTS) e Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 09/15/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 9997cf254a6d7e2f01f846e76ae82d20db748e84
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38030979"
---
# <a name="claims-to-windows-token-service-c2wts-and-reporting-services"></a>Attestazioni per il servizio token Windows (C2WTS) e Reporting Services

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

La visualizzazione di report in modalità nativa all'interno della [web part Visualizzatore di report di SQL Server Reporting Services](../report-server-sharepoint/deploy-report-viewer-web-part.md) richiede il componente Attestazioni per il servizio token Windows (C2WTS) di SharePoint.

C2WTS è inoltre necessario con la modalità SharePoint di SQL Server Reporting Services se si vuole usare l'autenticazione di Windows per le origini dati all'esterno della farm di SharePoint. Il servizio C2WTS è necessario anche se l'origine dati si trova nello stesso computer del servizio condiviso, sebbene in questo scenario la delega vincolata non sia richiesta.

> [!NOTE]
> L'integrazione di Reporting Services con SharePoint non è più disponibile nelle versioni successive a SQL Server 2016.

## <a name="report-viewer-web-part-configuration"></a>Configurazione della web part Visualizzatore di report

La web part Visualizzatore di report può essere usata per incorporare i report in modalità nativa di SQL Server Reporting Services nel sito di SharePoint. Questa web part è disponibile per SharePoint 2013 e SharePoint 2016. SharePoint 2013 e SharePoint 2016 usano l'autenticazione delle attestazioni. SQL Server Reporting Services (modalità nativa) usa l'autenticazione di Windows per impostazione predefinita. Di conseguenza, per il rendering corretto dei report, è necessario configurare C2WTS in modo appropriato.

## <a name="sharepoint-mode-integaration"></a>Integrazione della modalità SharePoint

**Questa sezione si applica solo a SQL Server 2016 Reporting Services e versioni precedenti.**

Il componente Attestazioni per il servizio token Windows (C2WTS) di SharePoint è necessario con la modalità SharePoint di SQL Server Reporting Services se si vuole usare l'autenticazione di Windows per le origini dati all'esterno della farm di SharePoint. La condizione è valida anche se l'utente accede alle origini dati tramite l'autenticazione di Windows perché la comunicazione tra il Web front-end (WFE) e il servizio condiviso Reporting Services si basa sempre sull'autenticazione delle attestazioni.

## <a name="steps-needed-to-configure-c2wts"></a>Passaggi necessari per configurare c2WTS

I token creati da C2WTS funzioneranno solo con delega vincolata (vincoli a servizi specifici) e l'opzione di configurazione "Utilizza un qualsiasi protocollo di autenticazione". Come notato in precedenza, se le origini dati si trovano nello stesso computer del servizio condiviso, la delega vincolata non è necessaria.

Se l'ambiente utilizzerà la delega vincolata Kerberos, le origini dati esterne e il servizio SharePoint Server devono trovarsi nello stesso dominio Windows. Qualsiasi servizio basato su Attestazioni per il servizio token Windows (c2WTS) deve usare la delega **vincolata** Kerberos per consentire a c2WTS di usare la transizione del protocollo Kerberos per convertire le attestazioni in credenziali di Windows. Questi requisiti sono validi per tutti i servizi condivisi SharePoint. Per altre informazioni, vedere [Pianificare l'autenticazione Kerberos in SharePoint 2013](http://technet.microsoft.com/library/ee806870.aspx).  

1. Configurare l'account del servizio C2WTS. Aggiungere l'account del servizio al gruppo di amministratori locale in ogni server in cui si userà C2WTS.

    Per la **web part Visualizzatore di report** saranno i server Web front-end (WFE). Per la **modalità integrata SharePoint** saranno i server applicazioni in cui è in esecuzione il servizio Reporting Services.

2. Configurare la delega per l'account del servizio C2WTS.

    L'account necessita della delega vincolata con transizione di protocollo e delle autorizzazioni per la delega ai servizi con cui deve comunicare, ovvero il motore di database di SQL Server e SQL Server Analysis Services. Per configurare la delega è possibile usare lo snap-in Utenti e computer di Active Directory ed è necessario essere un amministratore di dominio.

    > [!IMPORTANT]
    > Qualsiasi impostazione configurata per l'account del servizio C2WTS nella scheda relativa alla delega deve corrispondere all'account del servizio principale in uso. Per la **web part Visualizzatore di report** sarà l'account del servizio per l'applicazione Web SharePoint. Per la **modalità integrata SharePoint** sarà l'account del servizio Reporting Services.
    >
    > Se ad esempio si consente all'account del servizio C2WTS la delega a un servizio SQL, la stessa operazione dovrà essere eseguita sull'account del servizio Reporting Services per la modalità integrata SharePoint.

    * Fare clic con il pulsante destro del mouse su ogni account del servizio e aprire la finestra di dialogo delle proprietà. Nella finestra di dialogo fare clic sulla scheda **Delega** .

        La scheda relativa alla delega è visibile solo se all'oggetto è stato assegnato un nome dell'entità servizio (SPN). C2WTS non richiede un nome SPN nel proprio account. Tuttavia, senza questo nome, la scheda **Delega** non sarà visibile. Un modo alternativo per configurare la delega vincolata consiste nell'impiego di un'utilità, ad esempio **ADSIEdit**.

    * Di seguito vengono indicate le opzioni di configurazione principali nella scheda relativa alla delega:

        * Selezionare **Utente attendibile per la delega solo ai servizi specificati**
        * Selezionare **Usa un qualsiasi protocollo di autenticazione**

    * Selezionare **Aggiungi** per aggiungere un servizio per la delega.

    * Selezionare **Utenti o computer...*** e immettere l'account che ospita il servizio. Ad esempio, se SQL Server è in esecuzione con un account denominato *sqlservice*, immettere `sqlservice`. 

    * Selezionare l'elenco del servizio. Verranno visualizzati i nomi SPN disponibili per tale account. Se non viene visualizzato, il servizio indicato per l'account può essere mancante o inserito in un altro account. è possibile usare l'utilità SetSPN per modificare i nomi SPN.

    * Selezionare OK per uscire dalle finestre di dialogo.

3. Configurare *AllowedCallers* per C2WTS.

    In C2WTS è necessario che le identità chiamanti siano elencate esplicitamente nel file di configurazione **C2WTShost.exe.config**. C2WTS non accetta richieste da tutti gli utenti autenticati nel sistema, a meno che venga non venga configurato appositamente. In questo caso il chiamante è il gruppo di Windows WSS_WPG. Il file C2WTShost.exe.config viene salvato nel percorso seguente:

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

4. Avviare Attestazioni per il servizio token Windows tramite Amministrazione centrale SharePoint nella pagina **Gestisci servizi nel server**. Il servizio deve essere avviato nel server che eseguirà l'azione. Ad esempio, in presenza di un server WFE e di un server applicazioni in cui è in esecuzione il servizio condiviso SQL Server Reporting Services, sarà sufficiente avviare C2WTS solo nel server applicazioni. La presenza di C2WTS è necessaria in un server WFE solo se si esegue la web part Visualizzatore di report.

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
