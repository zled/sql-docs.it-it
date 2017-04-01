---
title: "Work Around the Excel 2003 Row Limitation | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a4c8700b-bef5-4440-a99c-bba5dcc46bfd
caps.latest.revision: 12
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 10
---
# Work Around the Excel 2003 Row Limitation
  In questo argomento viene illustrato come risolvere il limite di righe di Excel 2003 quando si esportano i report impaginati in Excel. La soluzione alternativa consiste in un report contenente una sola tabella.  
  
> [!IMPORTANT]  
>  L'estensione per il rendering di [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2003 è deprecata. Per altre informazioni, vedere [Funzionalità deprecate di SQL Server Reporting Services in SQL Server 2016](../Topic/Deprecated%20Features%20in%20SQL%20Server%20Reporting%20Services%20in%20SQL%20Server%202016.md).  
  
 Excel 2003 supporta un massimo di 65.536 righe per foglio di lavoro. È possibile risolvere questo limite forzando un'interruzione di pagina esplicita dopo un determinato numero di righe. Tramite il renderer Excel viene creato un nuovo foglio di lavoro per ogni interruzione di pagina esplicita.  
  
### Per creare un'interruzione di pagina esplicita  
  
1.  Aprire il report in [!INCLUDE[ss_dtbi](../../includes/ss-dtbi-md.md)] o nel portale Web [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
2.  Fare clic con il pulsante destro del mouse sulla riga dei dati nella tabella, quindi scegliere **Aggiungi gruppo** > **Gruppo padre** per aggiungere un gruppo di tabelle esterno.  
  
     ![Selezionare il gruppo padre](../../reporting-services/report-builder/media/datarow-selectparentgroup.png "Selezionare il gruppo padre")  
  
3.  Immettere la formula seguente nella casella dell'espressione **Raggruppa per** , quindi fare clic su **OK** per aggiungere il gruppo padre.  
  
     =Int((RowNumber(Nothing)-1)/65000)  
  
     La formula assegna un numero a ogni set di 65000 righe nel set di dati. Se si definisce un'interruzione di pagina per il gruppo, si ottiene un'interruzione di pagina ogni 65000 righe.  
  
     Con l'aggiunta del gruppo di tabelle esterno viene aggiunta una colonna di gruppo al report.  
  
4.  Per eliminare la colonna di gruppo, fare clic con il pulsante destro del mouse sull'intestazione di colonna, fare clic su **Elimina colonne**, selezionare **Elimina solo colonne**, quindi scegliere **OK**.  
  
     ![Eliminare una colonna di gruppo](../../reporting-services/report-builder/media/groupcolumn-delete-updated.png "Eliminare una colonna di gruppo")  
  
5.  Fare clic con il pulsante destro del mouse su **Gruppo 1** nella sezione **Gruppi di righe** , quindi scegliere **Proprietà gruppo**.  
  
     ![Visualizza proprietà di gruppo](../../reporting-services/report-builder/media/groupproperties-updated.png "Visualizza proprietà di gruppo")  
  
6.  Nella pagina **Ordinamento** della finestra di dialogo **Proprietà gruppo** selezionare l'opzione di ordinamento predefinita e fare clic su **Elimina**.  
  
     ![Elimina ordinamento predefinito](../../reporting-services/report-builder/media/groupproperties-sorting-updated.png "Elimina ordinamento predefinito")  
  
7.  Nella pagina **Interruzioni di pagina** fare clic su **Tra ogni istanza di un gruppo** , quindi scegliere **OK**.  
  
     ![Imposta interruzioni di pagina](../../reporting-services/report-builder/media/groupproperties-pagebreaks-updated.png "Imposta interruzioni di pagina")  
  
8.  Salvare il report. Quando lo si esporta in Excel, viene esportato in più fogli di lavoro, ognuno con un massimo di 65000 righe.  
  
  