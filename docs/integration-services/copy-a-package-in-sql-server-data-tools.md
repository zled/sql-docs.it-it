---
title: Copiare un pacchetto in SQL Server Data Tools | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages [Integration Services], copying
- copying packages
- regenerating package GUID
- updating package properties
ms.assetid: 03edc659-e76d-48c0-a749-5f1899b6b507
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 59a001e0aa360183e5e393faedc613cfabda0f02
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="copy-a-package-in-sql-server-data-tools"></a>Copiare un pacchetto in SQL Server Data Tools
  Questo argomento descrive come creare un nuovo pacchetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tramite la copia di un pacchetto esistente e come aggiornare le proprietà **Name** e **GUID** del nuovo pacchetto.  
  
### <a name="to-copy-a-package"></a>Per copiare un pacchetto  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] contenente il pacchetto che si desidera copiare.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto.  
  
3.  Verificare che il pacchetto da copiare sia selezionato in Esplora soluzioni o che la scheda attiva in Progettazione SSIS sia quella che contiene il pacchetto.  
  
4.  Nel **File** menu, fare clic su **salvare \<nome pacchetto > come**.  
  
    > [!NOTE]  
    >  Il comando **Salva con nome** è disponibile nel menu **File** solo se il pacchetto è aperto in Progettazione SSIS.  
  
5.  Facoltativamente, passare a un'altra cartella.  
  
6.  Modificare il nome del file del pacchetto, ricordando di mantenere l'estensione dtsx.  
  
7.  Fare clic su **Salva**.  
  
8.  Quando richiesto specificare se aggiornare il nome dell'oggetto di pacchetto in modo che corrisponda al nome del file. Se si sceglie **Sì**, la proprietà **Name** del pacchetto verrà aggiornata. Il nuovo pacchetto viene aggiunto al progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] e aperto in Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
9. Facoltativamente, fare clic sullo sfondo della scheda **Flusso di controllo** e quindi su **Proprietà**.  
  
10. Nella finestra Proprietà fare clic sul valore della proprietà ID, quindi nell'elenco a discesa fare clic su  **\<Genera nuovo ID >**.  
  
11. Scegliere **Salva elementi selezionati** dal menu **File** per salvare il nuovo pacchetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare una copia di un pacchetto](http://msdn.microsoft.com/library/21482a20-e420-4452-b7eb-8f9fa1929f31)   
 [Creazione di pacchetti in SQL Server Data Tools](../integration-services/create-packages-in-sql-server-data-tools.md)   
 [Integration Services &#40; SSIS &#41; Pacchetti](../integration-services/integration-services-ssis-packages.md)  
  
  

