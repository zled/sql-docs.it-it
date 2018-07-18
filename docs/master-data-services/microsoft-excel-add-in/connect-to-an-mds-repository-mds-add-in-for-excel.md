---
title: Connettersi a un repository MDS (componente aggiuntivo MDS per Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.component: microsoft-excel-add-in
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
caps.latest.revision: 12
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: c2e42b0d9567fc8cae85c9134e9169011fdf520d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="connect-to-an-mds-repository-mds-add-in-for-excel"></a>Connettersi a un repository MDS (componente aggiuntivo MDS per Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]è necessario connettersi a un repository MDS prima che sia possibile caricare o pubblicare dati.  
  
## <a name="prerequisites"></a>Prerequisites  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** .  
  
### <a name="to-connect-to-an-mds-repository"></a>Per connettersi a un repository MDS  
  
1.  In MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]nella scheda **Dati master** nel gruppo **Connetti e carica** fare clic sulla freccia sotto il pulsante **Connetti** e fare clic su **Gestisci connessioni**.  
  
2.  Nella finestra di dialogo **Gestisci connessioni** nella sezione **Nuova connessione** fare clic su **Crea una nuova connessione**.  
  
3.  Fare clic su **Nuovo**.  
  
4.  Nella finestra di dialogo **Aggiungi nuova connessione** nel campo **Descrizione** , digitare una descrizione per la connessione. Questa connessione sarà visualizzata quando si fa clic sulla freccia sotto il pulsante **Connetti** sulla barra degli strumenti.  
  
5.  Nella casella **Indirizzo server MDS** immettere l'URL dell'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], ad esempio `http://contoso/mds`.  
  
    > [!NOTE]  
    >  Assicurarsi che venga utilizzato il nome del computer e non "localhost".  
  
6.  Fare clic su **OK**. Il nome viene visualizzato nella sezione **Connessioni esistenti** .  
  
7.  Facoltativamente, fare clic su **Test** per verificare la connessione. Una conferma o un finestra di dialogo di errore viene visualizzata. Fare clic su **OK** per chiuderla.  
  
8.  Fare clic su **Connetti**. Viene visualizzato il riquadro **Master Data Services** .  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Esportare dati in Excel da Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)  
  
-   [Filtrare i dati prima dell'esportazione &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Connessioni &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/connections-mds-add-in-for-excel.md)  
  
  
