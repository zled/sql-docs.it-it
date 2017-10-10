---
title: Distribuire la web part di Visualizzatore Report di SQL Server Reporting Services in un sito di SharePoint | Documenti Microsoft
ms.custom: 
ms.date: 10/05/2017
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
ms.openlocfilehash: a75ad193204e17e1d053aa4e00adba5f551d684b
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---

# <a name="deploy-the-sql-server-reporting-services-report-viewer-web-part-on-a-sharepoint-site"></a>Distribuire la web part di Visualizzatore Report di SQL Server Reporting Services in un sito di SharePoint

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

La web part Visualizzatore Report è una parte web personalizzato che può essere usata per visualizzare i report di SQL Server Reporting Services (modalità nativa) all'interno del sito di SharePoint. È possibile utilizzare la web part per visualizzare, esplorare, stampare ed esportare report in un server di report. La web part Visualizzatore Report è associata a file di definizione (con estensione rdl) del report che vengono elaborati da un server di report di SQL Server Reporting Services o un Server di Report di Power BI. Questa web part Visualizzatore Report non può essere utilizzata con i report di Power BI ospitati nel Server di Report di Power BI.

Utilizzare le istruzioni seguenti per distribuire manualmente il pacchetto della soluzione che aggiungono la web part Visualizzatore Report in un ambiente SharePoint Server 2013 o SharePoint Server 2016. La distribuzione della soluzione è un passaggio obbligatorio per la configurazione della web part.

**La web part Visualizzatore Report è un pacchetto della soluzione autonoma e non è associata la modalità integrata SharePoint per SQL Server Reporting Services.**

## <a name="requirements"></a>Requisiti

**Supporta le versioni di SharePoint Server:**  
* SharePoint Server 2016
* SharePoint Server 2013

**Supporta le versioni di Reporting Services:**  
* SQL Server 2008 Reporting Services (modalità nativa) e versioni successive.
* Server di report di Power BI

## <a name="download-the-report-viewer-web-part-solution-package"></a>Scaricare il pacchetto di soluzione web part di Visualizzatore Report

La web part Visualizzatore Report è disponibile nel Microsoft Download Center.

[Scarica pacchetto della soluzione web part Visualizzatore Report](https://www.microsoft.com/download/details.aspx?id=55949)

## <a name="deploy-the-farm-solution"></a>Distribuire la soluzione farm

In questa sezione viene illustrato come distribuire il pacchetto della soluzione per la farm di SharePoint. È necessario eseguire questa attività una sola volta.

1. In un server SharePoint, aprire una Shell di gestione di SharePoint tramite il **Esegui come amministratore** opzione.

2. Eseguire [Add-SPSolution](https://technet.microsoft.com/library/ff607552(v=office.16).aspx) per aggiungere la soluzione farm.

    ```
    Add-SPSolution –LiteralPath "{path to file}\ReportViewerWebPart.wsp"
    ```

    Il cmdlet restituisce il nome e l'ID della soluzione e Deployed=False. Nel passaggio successivo la soluzione verrà distribuita.

3. Eseguire il [Install-SPSolution](https://technet.microsoft.com/library/ff607534(v=office.16).aspx) cmdlet per distribuire la soluzione farm.

    **SharePoint 2013**

    ```
    Install-SPSolution –Identity ReportViewerWebPart.wsp -CompatibilityLevel "14,15" -GACDeployment -WebApplication {URL to web application}
    ```

    **SharePoint 2016**

    ```
    Install-SPSolution –Identity ReportViewerWebPart.wsp -GACDeployment -WebApplication {URL to web application}
    ```

## <a name="activate-feature"></a>Consente di attivare funzionalità

1. Nel sito di SharePoint, selezionare il **ingranaggio** icona in alto a sinistra e selezionare **Impostazioni sito*.

    ![Impostazioni del sito dall'icona dell'ingranaggio.](media/sharepoint-site-settings.png)

    Per impostazione predefinita, l'accesso alle applicazioni Web SharePoint viene effettuato tramite la porta 80. Ciò significa che è possibile accedere spesso a un sito di SharePoint immettendo *http://<computer name>*  per aprire la raccolta siti radice.

3. In **Amministrazione raccolta siti**selezionare **caratteristiche raccolta siti**.

4. Scorrere verso il basso la pagina fino a individuare il **web part Visualizzatore Report** funzionalità.

5. Selezionare **Attiva**.

    ![Attivare la funzionalità di web part Visualizzatore Report](media/web-part-activiate-feature.png)

6. Ripetere per le raccolte siti aggiuntive aprendo ogni sito e fare clic su Azioni sito.

Facoltativamente, è possibile utilizzare PowerShell per abilitare questa funzionalità in tutti i siti utilizzando la [Enable-SPFeature](https://technet.microsoft.com/library/ff607803.aspx) cmdlet.

```
Get-SPWebApplication "<web application url>" | Get-SPSite -Limit ALL | 
        ForEach-Object {
            Write-Host "Enabling feature for $($_.URL)"
            Enable-SPFeature -identity "ReportViewerWebPart" -URL $_.URL -ErrorAction Continue
        }
```

## <a name="remove-the-solution"></a>Rimuovere la soluzione

Sebbene Amministrazione centrale SharePoint consenta il ritiro della soluzione, non è necessario ritirare il **ReportViewerWebPart.wsp** file a meno che non si sistematicamente risoluzione di problemi di distribuzione di installazione o di patch.

1. In Amministrazione centrale SharePoint, in **le impostazioni di sistema**selezionare **Gestisci soluzioni farm**.

2. Selezionare **ReportViewerWebPart.wsp**.

3. Selezionare Ritira soluzione.

### <a name="remove-the-web-part-from-site-settings"></a>Rimuovere la web part da impostazioni sito

Ritiro della soluzione non rimuove la web part Visualizzatore Report nell'elenco delle web part all'interno del sito di SharePoint. Per rimuovere la web part Visualizzatore Report, effettuare le operazioni seguenti.

1. Nel sito di SharePoint, selezionare il **ingranaggio** icona in alto a sinistra e selezionare **Impostazioni sito*.

    ![Impostazioni del sito dall'icona dell'ingranaggio.](media/sharepoint-site-settings.png)

    Per impostazione predefinita, l'accesso alle applicazioni Web SharePoint viene effettuato tramite la porta 80. Ciò significa che è possibile accedere spesso a un sito di SharePoint immettendo *http://<computer name>*  per aprire la raccolta siti radice.

2. In **raccolte Designer Web**selezionare **web part**.

3. Selezionare il **icona Modifica** accanto a **ReportViewerNativeMode.dwp**. Potrebbe non essere elencato nella prima pagina di risultati.

4. Selezionare **eliminare elemento**.

    ![Modificare ed eliminare la web part modalità nativa di Visualizzatore Report](media/report-viewer-native-mode-edit-delete.png)

È possibile tentare l'eliminazione della web part tramite PowerShell, ma non c'è un comando diretto per tale. Per un esempio di script, vedere [come eliminare una web part dalla raccolta web part](https://gallery.technet.microsoft.com/office/How-to-delete-Web-Parts-1132701f).

## <a name="supported-languages"></a>Lingue supportate

Con la web part sono supportate le lingue seguenti:

* Inglese (en)
* Tedesco (Germania)
* Spagnolo (sp)
* Francese (fr)
* Italiano (it)
* Giapponese (ja)
* Coreano (ko)
* Portoghese (pt)
* Russo (ru)
* Cinese (semplificato - zh-HANS e zh-CHS)
* Cinese (tradizionale, zh-HANT e zh-CHT)

## <a name="next-steps"></a>Passaggi successivi

Dopo aver distribuito web part di Visualizzatore di Report e activiated, è possibile aggiungere la web part a una pagina di SharePoint. Per ulteriori informazioni, vedere [web part Visualizzatore di Report aggiunta a una pagina di SharePoint](add-report-viewer-web-part-to-page.md).

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
