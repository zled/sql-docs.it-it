---
title: Eseguire il mapping di colonne ai domini compositi | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9422412-8a3d-45ae-af7f-072c902a09ba
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8a8f24f9808d184229cb85be5ddc88d0102f2ee7
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="map-columns-to-composite-domains"></a>Eseguire il mapping delle colonne ai domini compositi
  Un dominio composito è costituito da due o più singoli domini. È possibile eseguire il mapping di più colonne oppure di una singola colonna con valori delimitati al dominio.  
  
 Se sono disponibili più colonne, è necessario eseguire il mapping di una colonna a ogni singolo dominio nel dominio composito per applicare le regole di quest'ultimo alla pulizia dati. Selezionare i singoli domini inclusi nel dominio composito nel client Data Quality. Per altre informazioni, vedere [Creare un dominio composito](../../../data-quality-services/create-a-composite-domain.md).  
  
 Se è disponibile una singola colonna con valori delimitati, è necessario eseguire il mapping della singola colonna al dominio composito. I valori devono essere visualizzati nello stesso ordine dei singoli domini nel dominio composito. Il delimitatore nell'origine dati deve corrispondere al delimitatore utilizzato per analizzare i valori del dominio composito. È possibile selezionare il delimitatore per il dominio composito, nonché impostare altre proprietà nel client Data Quality. Per altre informazioni, vedere [Creare un dominio composito](../../../data-quality-services/create-a-composite-domain.md).  
  
### <a name="to-map-multiple-columns-to-a-composite-domain"></a>Per eseguire il mapping di più colonne a un dominio composito  
  
1.  Fare clic con il pulsante destro del mouse sulla trasformazione DQS Cleansing e quindi scegliere **Modifica**.  
  
2.  Nella scheda **Gestione connessione** verificare che il dominio composito sia visualizzato nell'elenco dei domini disponibili.  
  
3.  Nella scheda **Mapping** selezionare le colonne nell'area **Colonne di input disponibili** .  
  
4.  Per ogni colonna elencata nel campo **Colonna di input** selezionare un singolo dominio nel campo **Dominio** . Selezionare solo singoli domini disponibili nel dominio composito.  
  
5.  In base alle esigenze, modificare i nomi visualizzati nei campi **Alias di origine**, **Alias di output**e **Alias di stato** .  
  
6.  In base alle esigenze, impostare le proprietà nella scheda **Avanzate** . Per altre informazioni sulle proprietà, vedere [Finestra di dialogo Editor trasformazione DQS Cleansing](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
### <a name="to-map-a-column-with-delimited-values-to-a-composite-domain"></a>Per eseguire il mapping di una colonna con valori delimitati a un dominio composito  
  
1.  Fare clic con il pulsante destro del mouse sulla trasformazione DQS Cleansing e quindi scegliere **Modifica**.  
  
2.  Nella scheda **Gestione connessione** verificare che il dominio composito sia visualizzato nell'elenco dei domini disponibili.  
  
3.  Nella scheda **Mapping** selezionare la colonna nell'area **Colonne di input disponibili** .  
  
4.  Per la colonna elencata nel campo **Colonna di input** selezionare il dominio composito nel campo **Dominio** .  
  
5.  In base alle esigenze, modificare i nomi visualizzati nei campi **Alias di origine**, **Alias di output**e **Alias di stato** .  
  
6.  In base alle esigenze, impostare le proprietà nella scheda **Avanzate** . Per altre informazioni sulle proprietà, vedere [Finestra di dialogo Editor trasformazione DQS Cleansing](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Trasformazione DQS Cleansing](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)  
  
  
