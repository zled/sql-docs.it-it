---
title: Combinare i dati (componente aggiuntivo MDS per Excel) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f882bcd5aeead1dea06619598d868ded6c717167
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36065160"
---
# <a name="combine-data-mds-add-in-for-excel"></a>Combinare i dati (componente aggiuntivo MDS per Excel)
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]è possibile combinare i dati di due fogli di lavoro quando si desidera confrontare i dati prima della pubblicazione. In questa procedura verranno combinati i dati di due fogli di lavoro in un unico foglio. Sarà quindi possibile eseguire ulteriori confronti e determinare quali dati eventualmente pubblicare nel repository MDS.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
-   È necessario disporre di un foglio di lavoro contenente dati gestiti da MDS. Per altre informazioni, vedere [caricare i dati da MDS in Excel](export-data-to-excel-from-master-data-services.md).  
  
-   È necessario disporre di un foglio di lavoro contenente i dati che si desidera combinare con i dati gestiti da MDS. In questo foglio deve essere presente una riga di intestazione.  
  
### <a name="to-combine-non-managed-data-into-an-mds-managed-sheet"></a>Per combinare dati non gestiti in un foglio gestito da MDS  
  
1.  Nel foglio contenente i dati gestiti da MDS fare clic su **Combina dati** nel gruppo **Pubblica e convalida**.  
  
2.  Nella finestra di dialogo **Combina dati** fare clic sull'icona accanto alla casella di testo **Intervallo da combinare con dati MDS** . La finestra di dialogo verrà ridotta.  
  
3.  Fare clic sul foglio contenente i dati che si desidera combinare.  
  
4.  Evidenziare tutte le celle nel foglio che si desidera combinare, inclusa la riga di intestazione.  
  
5.  Nella finestra di dialogo **Combina dati** fare clic sull'icona. La finestra di dialogo verrà espansa.  
  
6.  Per una colonna elencata per l'entità MDS, selezionare una colonna in **Colonna corrispondente**. Tutte le colonne MDS non necessitano di colonne corrispondenti.  
  
7.  Fare clic su **Combina**. Verrà visualizzata una colonna **ORIGINE** , che indica se i dati provengono da MDS o da un'origine esterna.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
-   Per trovare le analogie tra i dati gestiti da MDS e i dati esterni, vedere [Cercare la corrispondenza tra dati simili &#40;componente aggiuntivo MDS per Excel&#41;](match-similar-data-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Il caricamento dei dati &#40;componente aggiuntivo MDS per Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Corrispondenza Data Quality nel componente aggiuntivo MDS per Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  