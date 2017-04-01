---
title: "Riordinare le colonne (componente aggiuntivo MDS per Excel) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac00462e-c0f7-4b8d-86f2-d9eda2598a15
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# Riordinare le colonne (componente aggiuntivo MDS per Excel)
  Nel [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], è possibile riordinare le colonne filtrando l'elenco prima del caricamento.  
  
 Quando si riordinano gli attributi di **filtro** la finestra di dialogo, i dati verrà caricata in Excel con il nuovo ordine. Tuttavia, quando si filtrano i dati dell'attributo la volta successiva, verrà ripristinato l'ordine della progettazione originale. Per modificare l'ordine in modo permanente, un amministratore deve modificare l'ordine nel **Amministrazione sistema** area di gestione dati Master. Per ulteriori informazioni, vedere [modificare l'ordine degli attributi](../../master-data-services/change-the-order-of-attributes.md).  
  
## Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** .  
  
### Per riordinare le colonne gestite da MDS  
  
1.  Aprire Excel e il **dati Master** scheda, connettersi a un repository MDS. Per ulteriori informazioni, vedere [connettersi a un Repository MDS & #40; Il componente aggiuntivo MDS per Excel & #41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  Nel **Esplora dati Master** riquadro, selezionare un modello e versione. L'elenco di entità viene popolato.  
  
    -   Se il **Esplora dati Master** riquadro non è visibile, il **Connetti e carica** gruppo, fare clic su **Mostra Esplora**.  
  
    -   Se il **Esplora dati Master** riquadro è disabilitato, perché il foglio esistente contiene già dati gestiti da MDS. Per abilitare il riquadro, aprire un nuovo foglio di lavoro.  
  
3.  Nel **Esplora dati Master** riquadro, fare clic su un'entità.  
  
4.  Nel **Connetti e carica** gruppo, fare clic su **filtro**.  
  
5.  Nel **filtro** della finestra di dialogo di **colonne** sezione nell'elenco di attributi, fare clic sull'attributo che si desidera spostare.  
  
6.  A destra dell'elenco, fare clic su di **di** o **verso il basso** sulla freccia per spostare l'attributo a sinistra e a destra nel foglio di lavoro.  
  
7.  Ripetere il passaggio 7 per ogni attributo fino a che l'ordine dall'alto in basso rappresenta l'ordine da sinistra a destra che si desidera nel foglio di lavoro.  
  
8.  Fare clic su **caricare i dati**. Il foglio viene popolato con dati gestiti da MDS e le colonne vengono visualizzate nell'ordine specificato.  
  
## Vedere anche  
 [Panoramica: Esportazione dei dati in Excel & #40; Il componente aggiuntivo MDS per Excel & #41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
  