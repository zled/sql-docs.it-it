---
title: Aggiungere web part di Visualizzatore Report di SQL Server Reporting Services a una pagina di SharePoint | Documenti Microsoft
ms.custom: Display a report, from SQL Server Reporting Services or Power BI Report Server, by adding a Report Viewer web part to a SharePoint page.
ms.date: 09/26/2017
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: ea362cd05de5d1ba17ca717d94354d5786119bab
ms.openlocfilehash: fbc68b6ff9f1edf5cf6ee13f6e93a3d2d1a8f834
ms.contentlocale: it-it
ms.lasthandoff: 10/06/2017

---

# <a name="add-sql-server-reporting-services-report-viewer-web-part-to-a-sharepoint-page"></a>Aggiungere web part di Visualizzatore Report di SQL Server Reporting Services a una pagina di SharePoint

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Visualizzare un report, da SQL Server Reporting Services o Server di Report di Power BI, mediante l'aggiunta di una web part Visualizzatore Report a una pagina di SharePoint.

![Web part Visualizzatore di report in una pagina di SharePoint](media/sharepoint-report-viewer-web-part-on-page.png)

## <a name="prerequisites"></a>Prerequisiti

* Per i report caricare correttamente, Claims nel servizio Token Windows (C2WTS) deve essere configurato per Kerberos per la delega vincolata. Per ulteriori informazioni su come configurare C2WTS, vedere [attestazioni per il servizio Token Windows (C2WTS) e Reporting Services](../install-windows/claims-to-windows-token-service-c2wts-and-reporting-services.md).

* La web part Visualizzatore di Report deve essere distribuita alla farm di SharePoint. Per informazioni su come distribuire il progetto di soluzione web part di Visualizzatore Report, vedere [distribuire la web part di Visualizzatore Report in un sito di SharePoint](deploy-report-viewer-web-part.md).

* Per aggiungere una web part a una pagina web, è necessario disporre dell'autorizzazione aggiunta e personalizzazione pagine a livello di sito. Se si usano impostazioni di sicurezza predefinite, questa autorizzazione è concessa ai membri del gruppo **Proprietari** che hanno il livello di autorizzazione Controllo completo.

## <a name="add-web-part"></a>Aggiunta di web part

1. Nel sito di SharePoint, selezionare il **ingranaggio** icona in alto a sinistra e selezionare **aggiungere una pagina**.

    ![Aggiungere una pagina a un sito di sharepoint dall'icona dell'ingranaggio.](media/sharepoint-add-a-page.png)

2. Assegnare alla pagina, un nome e selezionare **crea**.

3. Finestra di progettazione della pagina, selezionare il **inserire** scheda della barra multifunzione. Selezionare quindi **web part** all'interno di **parti** sezione.

    ![Inserire una web part dalla barra multifunzione di office.](media/sharepoint-insert-web-part.png)

4. In **categorie**selezionare **SQL Server Reporting Services (modalità nativa). In **parti**selezionare **Visualizzatore Report**. Selezionare quindi **Aggiungi**.

    ![Aggiungere una web part Visualizzatore Report.](media/sharepoint-report-viewer-web-part.png)

    Questa verifica può sembrare inizialmente con un errore. L'errore è perché l'URL del server di report predefinito è impostato su *http://localhost* e potrebbe non essere disponibile in tale posizione.

## <a name="configure-the-report-viewer-web-part"></a>Configurare la web part Visualizzatore Report

Per configurare la web part in modo da puntare al report specifico, eseguire le operazioni seguenti.

1. Quando si modifica la pagina di SharePoint, selezionare la freccia rivolta verso il basso in alto a destra della web part e selezionare **Modifica web part**.

    ![Pagina Modifica web part elenco a discesa.](media/sharepoint-edit-web-part.png)

2. Immettere il **URL Server di Report** del server di report che ospita il report. Questo dovrebbe essere simile a *http://myrsserver/reportserver*.

3. Immettere il percorso e il nome del report che si desidera visualizzare nella web part. Questo avrà un aspetto simile a *AdventureWorks Sample Reports/Company Sales*. In questo esempio, il report *Company Sales* è in una cartella denominata *AdventureWorks Sample Reports*.

4. Se il report richiede parametri, dopo che è stato fornito l'URL del server di report e il nome del report, selezionare **carica parametri** all'interno di **parametri** sezione.

5. Selezionare **Ok** per salvare le modifiche alla configurazione web part.

6. Selezionare **salvare**, all'interno della barra multifunzione di Office, per salvare le modifiche alla pagina di SharePoint.

![Web part Visualizzatore di report in una pagina di SharePoint](media/sharepoint-report-viewer-web-part-on-page.png)

## <a name="considerations-and-limitations"></a>Considerazioni e limitazioni

* La web part Visualizzatore Report può essere usata in moderne pagine all'interno di SharePoint.
* Report di Power BI non può essere utilizzato con la web part Visualizzatore Report.
* Se non viene visualizzata la web part di Visualizzatore Report, aggiungere alla pagina, accertarsi di avere [distribuito la web part Visualizzatore Report](deploy-report-viewer-web-part.md).

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)

