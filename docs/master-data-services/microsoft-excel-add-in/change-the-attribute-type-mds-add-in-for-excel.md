---
title: Modificare il tipo di attributo (componente aggiuntivo MDS per Excel) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d3001d9-8d0f-4e4a-8e04-4f666bf0df69
caps.latest.revision: 8
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: aafb37debc437fa6f2aee678eba571d8bd23ec5e
ms.contentlocale: it-it
ms.lasthandoff: 09/07/2017

---
# <a name="change-the-attribute-type-mds-add-in-for-excel"></a>Modificare il tipo di attributo (componente aggiuntivo MDS per Excel)
  Nel [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]gli amministratori possono modificare il tipo di attributo quando il tipo di dati o il numero di caratteri consentiti non è corretto.  
  
 Per modificare il tipo di attributo per creare un elenco vincolato (attributo basato su dominio), vedere [Creare un attributo basato su dominio &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/create-a-domain-based-attribute-mds-add-in-for-excel.md).  
  
> [!NOTE]  
>  Non è possibile aggiornare il tipo o la lunghezza delle colonne **Nome** o **Codice**.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione di accesso alle aree funzionali **Amministrazione sistema** e **Visualizzatore** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../../master-data-services/administrators-master-data-services.md).  
  
-   Devono essere disponibili un modello esistente, un'entità e un attributo.  
  
### <a name="to-change-the-attribute-type"></a>Per modificare il tipo di attributo  
  
1.  In Excel caricare l'entità contenente la colonna (attributo) che si desiderare modificare. Per altre informazioni, vedere [Esportare dati in Excel da Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md).  
  
2.  Fare clic su una cella nella colonna che si desidera modificare.  
  
3.  Nel gruppo **Compila modello** fare clic su **Proprietà attributi**.  
  
4.  Nella finestra di dialogo **Proprietà attributi** aggiornare le impostazioni in base alle necessità.  
  
5.  Scegliere **OK**.  
  
## <a name="what-happens-when-you-change-the-attribute-type"></a>Cosa accade quando si modifica il tipo di attributo  
 Se è presente una dipendenza dall'attributo, ad esempio se viene fatto riferimento all'attributo da una regola business MDS o da una gerarchia derivata, non è possibile modificare il tipo di dati dell'attributo. Viene visualizzato un errore che informa che il tipo di attributo non può essere modificato perché un oggetto vi fa riferimento.  
  
 Se si verifica un errore durante la conversione di un tipo di dati per i valori di attributo, MDS effettua le operazioni seguenti.  
  
-   Modifica il tipo di dati dell'attributo.  
  
-   Genera una copia dell'attributo con suffisso "_old" che contiene i valori precedenti. In questo caso si parla di attributo deprecato.  
  
## <a name="see-also"></a>Vedere anche  
 [Attributi &#40;Master Data Services&#41;](../../master-data-services/attributes-master-data-services.md)   
 [Compilazione di un modello &#40;componente aggiuntivo MDS per Excel&#41;](../../master-data-services/microsoft-excel-add-in/building-a-model-mds-add-in-for-excel.md)  
  
  

