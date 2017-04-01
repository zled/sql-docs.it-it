---
title: "Filtrare i dati prima dell&#39;esportazione (aggiuntivo MDS per Excel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# Filtrare i dati prima dell&#39;esportazione (aggiuntivo MDS per Excel)
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], filtrare i dati quando si desidera limitare le dimensioni e l'ambito dei dati che si siano esportando in Excel.  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** .  
  
### Per filtrare i dati prima dell'esportazione  
  
1.  Aprire Excel e il **dati Master** scheda, connettersi a un repository MDS. Per ulteriori informazioni, vedere [connettersi a un Repository MDS & #40; Il componente aggiuntivo MDS per Excel & #41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  Nel **Esplora dati Master** riquadro, selezionare un modello e versione. L'elenco di entità viene popolato.  
  
    -   Se il **Esplora dati Master** riquadro non è visibile, il **Connetti e carica** gruppo, fare clic su **Mostra Esplora**.  
  
    -   Se il **Esplora dati Master** riquadro è disabilitato, perché il foglio esistente contiene già dati gestiti da MDS. Per abilitare il riquadro, aprire un nuovo foglio di lavoro.  
  
3.  Nel **Esplora dati Master** riquadro, nell'elenco di entità, fare clic sull'entità che si desidera filtrare.  
  
4.  Sulla barra multifunzione, nel **Connetti e carica** gruppo, fare clic su **filtro**.  
  
5.  Completare il **filtro** la finestra di dialogo selezionando gli attributi (colonne) per visualizzare, impostare l'ordine delle colonne e se necessario, filtrando i dati in modo vengano restituite meno righe. Visualizzazione di **riepilogo** riquadro per la quantità di dati verrà restituito. Per ulteriori informazioni, vedere [la finestra di dialogo filtro & #40; Il componente aggiuntivo MDS per Excel & #41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md).  
  
6.  Fare clic su **caricare i dati**. Il foglio viene popolato con i dati gestiti da MDS.  
  
    > [!NOTE]  
    >  -   Solo il primo milione di membri viene caricato in Excel.  
    > -   Nelle colonne che sono elenchi vincolati (attributi basati su dominio) vengono caricati solo i primi 25000 valori per impostazione predefinita.  
  
## Passaggi successivi  
 [Importare dati da Excel per Master Data Services & #40; Il componente aggiuntivo MDS per Excel & #41;](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## Vedere anche  
 [Panoramica: Esportazione dei dati in Excel & #40; Il componente aggiuntivo MDS per Excel & #41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [La finestra di dialogo filtro & #40; Il componente aggiuntivo MDS per Excel & #41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [Riordinare le colonne & #40; Il componente aggiuntivo MDS per Excel & #41;](../../master-data-services/microsoft-excel-add-in/reorder-columns-mds-add-in-for-excel.md)  
  
  