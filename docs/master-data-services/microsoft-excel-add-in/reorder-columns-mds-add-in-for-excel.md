---
title: Riordinare le colonne (componente aggiuntivo MDS per Excel) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: microsoft-excel-add-in
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac00462e-c0f7-4b8d-86f2-d9eda2598a15
caps.latest.revision: "7"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bf0cd9b82e15ca3b6c099d1caa81ef8ec3757f31
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2017
---
# <a name="reorder-columns-mds-add-in-for-excel"></a>Riordinare le colonne (componente aggiuntivo MDS per Excel)
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]è possibile riordinare le colonne filtrando l'elenco prima del caricamento.  
  
 Quando si riordinano gli attributi nella finestra di dialogo **Filtro** , i dati vengono caricati in Excel con il nuovo ordine. Tuttavia, quando si filtrano i dati dell'attributo la volta successiva, verrà ripristinato l'ordine della progettazione originale. Per modificare l'ordine in modo permanente, è consigliabile che un amministratore modifichi l'ordine nell'area **Amministrazione sistema** di Gestione dati master. Per altre informazioni, vedere [Change the Order of Attributes](../../master-data-services/change-the-order-of-attributes.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** .  
  
### <a name="to-reorder-mds-managed-columns"></a>Per riordinare le colonne gestite da MDS  
  
1.  Aprire Excel e nella scheda **Dati master** connettersi a un repository MDS. Per altre informazioni, vedere [Connettersi a un repository MDS &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  Nel riquadro **Esplora dati master** selezionare un modello e una versione. L'elenco di entità viene popolato.  
  
    -   Se il riquadro **Esplora dati master** non è visibile, nel gruppo **Connetti e carica** fare clic su **Esplora dati master**.  
  
    -   Se il riquadro **Esplora dati master** è disabilitato, significa che il foglio esistente contiene già i dati gestiti da MDS. Per abilitare il riquadro, aprire un nuovo foglio di lavoro.  
  
3.  Nel riquadro **Esplora dati master** , fare clic su un'entità.  
  
4.  Nel gruppo **Connetti e carica** fare clic su **Filtro**.  
  
5.  Nella finestra di dialogo **Filtro** , nella sezione **Colonne** , nell'elenco di attributi fare clic sull'attributo che si desidera spostare.  
  
6.  A destra dell'elenco, fare clic sulla freccia **SU** o **GIÙ** per spostare l'attributo a sinistra o a destra nel foglio di lavoro.  
  
7.  Ripetere il passaggio 7 per ogni attributo fino a che l'ordine dall'alto in basso rappresenta l'ordine da sinistra a destra che si desidera nel foglio di lavoro.  
  
8.  Fare clic su **Carica dati**. Il foglio viene popolato con dati gestiti da MDS e le colonne vengono visualizzate nell'ordine specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica: Esportazione dei dati in Excel &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
  
