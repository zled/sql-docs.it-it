---
title: Connettersi a un repository MDS (componente aggiuntivo MDS per Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f427312-4c09-4c8b-b9f9-8b235557a74b
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 5c2fd145d78c4c24d9f43a5919d53af3c3aab3c6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36170365"
---
# <a name="connect-to-an-mds-repository-mds-add-in-for-excel"></a>Connettersi a un repository MDS (componente aggiuntivo MDS per Excel)
  In [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]è necessario connettersi a un repository MDS prima che sia possibile caricare o pubblicare dati.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** .  
  
### <a name="to-connect-to-an-mds-repository"></a>Per connettersi a un repository MDS  
  
1.  In MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]nella scheda **Dati master** nel gruppo **Connetti e carica** fare clic sulla freccia sotto il pulsante **Connetti** e fare clic su **Gestisci connessioni**.  
  
2.  Nella finestra di dialogo **Gestisci connessioni** nella sezione **Nuova connessione** fare clic su **Crea una nuova connessione**.  
  
3.  Fare clic su **Nuovo**.  
  
4.  Nella finestra di dialogo **Aggiungi nuova connessione** nel campo **Descrizione** , digitare una descrizione per la connessione. Questa connessione sarà visualizzata quando si fa clic sulla freccia sotto il pulsante **Connetti** sulla barra degli strumenti.  
  
5.  Nella casella **Indirizzo server MDS** immettere l'URL dell'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)], ad esempio http://contoso/mds.  
  
    > [!NOTE]  
    >  Assicurarsi che venga utilizzato il nome del computer e non "localhost".  
  
6.  Fare clic su **OK**. Il nome viene visualizzato nella sezione **Connessioni esistenti** .  
  
7.  Facoltativamente, fare clic su **Test** per verificare la connessione. Una conferma o un finestra di dialogo di errore viene visualizzata. Fare clic su **OK** per chiuderla.  
  
8.  Fare clic su **Connetti**. Viene visualizzato il riquadro **Master Data Services** .  
  
## <a name="next-steps"></a>Passaggi successivi  
  
-   [Caricare dati da MDS in Excel](export-data-to-excel-from-master-data-services.md)  
  
-   [Filtrare i dati prima del caricamento &#40;componente aggiuntivo MDS per Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Connessioni &#40;componente aggiuntivo MDS per Excel&#41;](connections-mds-add-in-for-excel.md)  
  
  