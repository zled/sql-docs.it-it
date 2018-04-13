---
title: Individuazione dati e classificazione SQL | Microsoft Docs
description: Individuazione dati e classificazione SQL
services: sql-server
documentationcenter: ''
author: giladm
manager: shaik
ms.reviewer: carlrab
ms.assetid: 89c2a155-c2fb-4b67-bc19-9b4e03c6d3bc
ms.service: sql-server
ms.custom: security
ms.workload: data-management
ms.tgt_pltfrm: na
ms.topic: article
ms.date: 02/13/2018
ms.author: giladm
ms.openlocfilehash: eee9d5b920f422d000fa4e9cb8b78924cb55b466
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2018
---
# <a name="sql-data-discovery-and-classification"></a>Individuazione dati e classificazione SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La funzionalità Individuazione dati e classificazione costituisce un nuovo strumento incorporato in SQL Server Management Studio (SSMS) per **l'individuazione**, **la classificazione**, **l'assegnazione di etichette** & **la creazione di report** di dati sensibili nei database.
L'individuazione e la classificazione dei dati più sensibili, come ad esempio i dati aziendali, finanziari, medici, personali e così via, possono avere un ruolo fondamentale nella protezione delle informazioni dell'organizzazione. Possono costituire l'infrastruttura per:
* Soddisfare i requisiti in materia di privacy e di conformità alle normative, come ad esempio l'RGPD (Regolamento generale sulla protezione dei dati).
* Controllare l'accesso e rafforzare la sicurezza di database o colonne contenenti dati altamente sensibili.


> [!NOTE]
> Individuazione dati e classificazione è una funzionalità **supportata per SQL Server 2008 e versioni successive**. Per database SQL di Azure, vedere [Individuazione dati e classificazione nel database SQL di Azure](https://go.microsoft.com/fwlink/?linkid=866265).

## <a id="subheading-1"></a>Panoramica
Individuazione dati e classificazione introduce un set di servizi avanzati, che costituisce un nuovo paradigma di Information Protection per SQL per proteggere i dati, non solo il database:
* **Individuazione e consigli**: il motore di classificazione esegue l'analisi del database e identifica le colonne che contengono dati potenzialmente sensibili. In seguito offre un modo semplice per verificare e applicare i consigli di classificazione appropriati, nonché per classificare manualmente le colonne.
* **Assegnazione di etichette**: è possibile contrassegnare le colonne con etichette di classificazione di riservatezza in modo permanente.
* **Visibilità**: è possibile visualizzare lo stato di classificazione del database in un report dettagliato che può essere stampato o esportato a scopo di controllo e conformità, nonché per altre esigenze.

## <a id="subheading-2"></a>Individuazione, classificazione e assegnazione di etichette a colonne di dati sensibili
Nella sezione seguente vengono descritti i passaggi per l'individuazione, la classificazione e l'assegnazione di etichette a colonne del database contenenti dati sensibili, nonché per visualizzare lo stato di classificazione corrente del database e per esportare report.

La classificazione include due attributi di metadati:
* Etichette: gli attributi di classificazione principali, usati per definire il livello di riservatezza dei dati archiviati nella colonna.  
* Tipi di informazioni: offrono maggiore granularità del tipo di dati archiviati nella colonna.

<br>
**Per classificare il database di SQL Server:**

1. in SQL Server Management Studio (SSMS) connettersi a SQL Server.

2. In Esplora oggetti di SSMS fare clic con il pulsante destro del mouse sul database che si vuole classificare e scegliere **Attività** > **Classifica dati**.

    ![Riquadro di spostamento][1]

3. Il motore di classificazione esegue l'analisi del database per identificare le colonne che contengono dati potenzialmente sensibili e specifica un elenco di **classificazioni di colonne consigliate**:

    * Per visualizzare l'elenco delle classificazioni delle colonne consigliate, fare clic sulla casella di notifica dei consigli in alto oppure sul pannello dei consigli nella parte inferiore della finestra:

        ![Riquadro di spostamento][2]

        ![Riquadro di spostamento][3]

    * Esaminare l'elenco dei consigli:
        * Per accettare un consiglio per una colonna specifica, selezionare la casella di controllo nella colonna sinistra della riga pertinente. È anche possibile contrassegnare *tutti i consigli* come accettati selezionando la casella di controllo nell'intestazione della tabella dei consigli.

        * È anche possibile modificare i valori di Tipo di informazioni e di Etichetta riservatezza mediante le caselle a discesa.        

        ![Riquadro di spostamento][4]

    * Per applicare i consigli selezionati, fare clic sul pulsante blu **Accettare i consigli selezionati**.

        ![Riquadro di spostamento][5]

4. È anche possibile **classificare manualmente** le colonne in alternativa o in aggiunta alla classificazione basata sui consigli:

    * Fare clic su **Aggiungi classificazione** nel menu superiore della finestra.

        ![Riquadro di spostamento][6]

    * Nella finestra di contesto che si apre selezionare lo schema, la tabella e la colonna che si vuole classificare, nonché il tipo di informazioni e l'etichetta di riservatezza. In seguito fare clic sul pulsante blu **Aggiungi classificazione** nella parte inferiore della finestra di contesto.

        ![Riquadro di spostamento][7]

5. Per completare la classificazione e assegnare in modo permanente le etichette alle colonne del database con i nuovi metadati di classificazione, fare clic su **Salva** nel menu superiore della finestra.

    ![Riquadro di spostamento][8]


6. Per generare un report con un riepilogo completo dello stato di classificazione del database, fare clic su **Visualizza Report** nel menu superiore della finestra.

    ![Riquadro di spostamento][9]

    ![Riquadro di spostamento][10]


## <a id="subheading-3"></a>Passaggi successivi

Per database SQL di Azure, vedere [Individuazione dati e classificazione nel database SQL di Azure](https://go.microsoft.com/fwlink/?linkid=866265).

Potrebbe essere consigliabile proteggere le colonne sensibili applicando meccanismi di sicurezza a livello di colonna:

* [Dynamic Data Masking](https://docs.microsoft.com/en-us/sql/relational-databases/security/dynamic-data-masking) per l'offuscamento delle colonne sensibili in uso.
* [Always Encrypted](https://docs.microsoft.com/en-us/sql/relational-databases/security/encryption/always-encrypted-database-engine) per la crittografia delle colonne sensibili inattive.

<!--Anchors-->
[SQL Data Discovery & Classification overview]: #subheading-1
[Discovering, classifying & labeling sensitive columns]: #subheading-2
[Next Steps]: #subheading-3

<!--Image references-->
[1]: ./media/sql-data-discovery-and-classification/1_data_classification_explorer_menu.png
[2]: ./media/sql-data-discovery-and-classification/2_recommendations_notification_box.png
[3]: ./media/sql-data-discovery-and-classification/3_recommendations_panel.png
[4]: ./media/sql-data-discovery-and-classification/4_recommendations.png
[5]: ./media/sql-data-discovery-and-classification/5_accept_recommendations_button.png
[6]: ./media/sql-data-discovery-and-classification/6_add_classification_button.png
[7]: ./media/sql-data-discovery-and-classification/7_manual_classification.png
[8]: ./media/sql-data-discovery-and-classification/8_save.png
[9]: ./media/sql-data-discovery-and-classification/9_view_report.png
[10]: ./media/sql-data-discovery-and-classification/10_report.png
