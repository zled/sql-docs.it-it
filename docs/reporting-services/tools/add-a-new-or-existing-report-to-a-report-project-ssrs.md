---
title: "Aggiungere un report nuovo o esistente a un progetto report (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "report [Reporting Services], creazione"
ms.assetid: 8bc0bb53-ad8a-464d-bb6a-7fea5fa62c5c
caps.latest.revision: 20
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 19
---
# Aggiungere un report nuovo o esistente a un progetto report (SSRS)
  Per aggiungere un nuovo report impaginato di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], è possibile usare la Creazione guidata report o aggiungere un nuovo report vuoto al progetto. È anche possibile aggiungere un report esistente. Dopo l'aggiunta di un report, il relativo nome verrà visualizzato nella cartella **Report** nel progetto.  
  
> [!NOTE]  
>  Per visualizzare in anteprima un report con le origini dati esistenti, è necessario disporre delle autorizzazioni per l'origine dati dal client di creazione report. Per altre informazioni, vedere l'articolo relativo a [connessioni dati, origini dati e stringhe di connessione](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md).  
  
 Dopo l'aggiunta di un report, è possibile definire origini dati e set di dati, nonché progettarne il layout. Per iniziare, vedere [Creare un report tabella semplice &#40;esercitazione su SSRS&#41;](../../reporting-services/create-a-basic-table-report-ssrs-tutorial.md) o [Tabelle &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md).  
  
## Per aggiungere un nuovo report tramite la Creazione guidata report  
  
1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella Report, quindi scegliere **Aggiungi nuovo report**. Verrà visualizzata la finestra di dialogo **Creazione guidata report**.  
  
     Tramite i passaggi della procedura guidata sarà possibile creare un'origine dati e un set di dati con una query, definire gruppi, specificare un layout, scegliere uno stile che include il colore e il tipo di carattere e creare il report. I passaggi includono:  
  
    -   **Selezione un'origine dati.** Il primo passaggio della creazione di un report consiste nel definire un'origine dati. Nella Creazione guidata report viene visualizzato un elenco di tutte le origini dei dati condivise disponibili nel progetto report, nonché un'opzione per la creazione di una nuova origine dei dati.  
  
    -   **Progettazione query.** Nel secondo passaggio si progetta la query. È possibile digitare la stringa della query, compilarla tramite Progettazione query o importare una query da un altro report. Per altre informazioni sugli strumenti di progettazione query, vedere [Strumenti di progettazione query in Reporting Services](../Topic/Reporting%20Services%20Query%20Designers.md).  
  
    -   **Selezione tipo di report.** Nel terzo passaggio si seleziona il tipo di report desiderato. È possibile selezionare un report tabulare o matrice. Un report tabella include un numero fisso di colonne. Un report matrice, o a campi incrociati, include un numero variabile di colonne in base ai risultati della query. In un report mappa i dati analitici vengono visualizzati su uno sfondo geografico.  
  
    -   **Scelta di uno stile.** In questo passaggio si applica uno stile al report tramite un modello di stili. Selezionare un modello per applicare stili di carattere, colore e bordo al report. In Progettazione report sono disponibili sei modelli di stile: Ardesia, Foresta, Aziendale, Grassetto, Oceano e Generico. È inoltre possibile aggiungere ulteriori modelli di stili.  
  
        > [!NOTE]  
        >  È possibile modificare i modelli esistenti o aggiungerne di nuovi modificando il file StyleTemplates.xml nella cartella \Programmi\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\Business Intelligence Wizards\Reports\Styles\\<lingua\>, dove \<lingua> è la lingua in uso. Ad esempio se si usa la versione in inglese di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], il nome della cartella è "EN". Questa cartella è disponibile nel computer in cui è installato Progettazione report. Sono disponibili due copie del file StyleTemplates.xml. Per modificare gli stili applicati tramite Creazione guidata report, modificare il file nella cartella creata per la lingua in uso.  
  
    -   **Assegnazione di un nome al report.**  Nell'ultimo passaggio della procedura guidata si assegna un nome al report e si verificano i campi che verranno inclusi nel report. Dopo il completamento di tutti i passaggi il report viene creato automaticamente e aggiunto al progetto server di report.  
  
## Per aggiungere un report vuoto  
  
1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
2.  In **Modelli** fare clic su **Report**.  
  
3.  Scegliere **Aggiungi**.  
  
     Un nuovo report vuoto verrà aggiunto al progetto e visualizzato nell'area di progettazione.  
  
## Per aggiungere un report esistente  
  
1.  Scegliere **Aggiungi** dal menu **Progetto**, quindi **Elemento esistente**.  
  
2.  Passare al percorso del file con estensione rdl, selezionarlo, quindi fare clic su **Aggiungi**.  
  
     l report verrà aggiunto al progetto nella cartella **Report**. Quando il progetto verrà chiuso e riaperto, i report verranno disposti in ordine alfabetico.  
  
## Vedere anche  
 [Esercitazioni su Reporting Services &#40;SSRS&#41;](../../reporting-services/reporting-services-tutorials-ssrs.md)  
  
  