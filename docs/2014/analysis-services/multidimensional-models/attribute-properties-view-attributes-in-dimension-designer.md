---
title: Visualizzare attributi in Progettazione dimensioni | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- displaying attributes
- attributes [Analysis Services], viewing
- viewing attributes
ms.assetid: 855bef07-b72d-4ce3-bf02-de77abeee71a
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c78e76030fe216df9e610b0e1ab6e6f37a652b30
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064809"
---
# <a name="view-attributes-in-dimension-designer"></a>Visualizzare attributi in Progettazione dimensioni
  Gli attributi vengono creati in oggetti dimensione. È possibile visualizzare e configurare gli attributi tramite Progettazione dimensioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Nel riquadro **Attributi** della scheda **Struttura dimensione** di Progettazione dimensioni sono elencati gli attributi inclusi in una dimensione. Utilizzare questo riquadro per aggiungere, rimuovere o configurare attributi. È inoltre possibile selezionare gli attributi da utilizzare come livello in una nuova gerarchia o da aggiungere come livello in una gerarchia esistente.  
  
 Per visualizzare gli attributi in una dimensione, aprire Progettazione dimensioni per tale dimensione. Nel riquadro **Attributi** della scheda **Struttura dimensione**  della finestra di progettazione vengono visualizzati gli attributi inclusi nella dimensione. È possibile passare da una visualizzazione elenco, albero o griglia scegliendo **Mostra attributi in** sul **dimensione** dal menu di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] e quindi fare clic su uno dei comandi illustrati nella tabella seguente.  
  
|Mostra attributi in|Description|  
|------------------------|-----------------|  
|**Elenco**|Consente di visualizzare gli attributi in formato di elenco.<br /><br /> Fare clic con il pulsante destro del mouse su un attributo per eliminarlo dall'elenco, rinominarlo oppure modificarne l'utilizzo.<br /><br /> Utilizzare questa visualizzazione per compilare gerarchie. Le informazioni sugli attributi e le proprietà membro non sono visibili.|  
|**Struttura ad albero**|Consente di visualizzare gli attributi in formato di albero, con la dimensione come nodo di livello principale dell'albero. Utilizzare questa visualizzazione per visualizzare e creare proprietà membro. Può inoltre essere utilizzata per compilare gerarchie. Espandere un attributo per visualizzarne le relazioni tra attributi o per creare una nuova relazione tra attributi, eseguendo le operazioni seguenti:<br /><br /> Fare clic sulla dimensione, su un attributo o su una proprietà membro per visualizzarne le proprietà nella finestra **Proprietà** .<br /><br /> Fare clic con il pulsante destro del mouse su una proprietà membro o su un attributo per eliminarlo dall'elenco, rinominarlo oppure modificarne l'utilizzo.|  
|**Griglia**|Consente di visualizzare gli attributi in formato di griglia. Fare clic su qualsiasi riga della griglia per visualizzare le proprietà dell'attributo.  Utilizzare questa visualizzazione per creare e configurare attributi. Nella griglia vengono visualizzate le colonne seguenti:<br /><br /> **Nome**: Mostra il valore di **nome** proprietà. Digitare un diverso nome per modificare l'impostazione.<br /><br /> **Utilizzo**: Specifica se si tratta di un attributo Regular, Key, padre o AccountType. Fare clic su un valore in questa colonna per selezionare un'impostazione diversa.<br /><br /> **Tipo**: specifica la categoria di business intelligence per l'attributo. Fare clic sulla cella per selezionare un'impostazione diversa.<br /><br /> **La colonna chiave**: Mostra il tipo di dati OLE DB per il **KeyColumn** proprietà dell'attributo. Questa colonna non può essere modificata.<br /><br /> **Nome colonna**: indica se il **NameColumn** impostazione della proprietà dell'attributo corrisponde alla colonna impostata per il **KeyColumn** proprietà. Questa colonna non può essere modificata.|  
  
 In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]gli attributi vengono contrassegnati in base al relativo utilizzo tramite le icone illustrate nella tabella seguente.  
  
|Icona|Utilizzo dell'attributo|  
|----------|---------------------|  
|![Icona di attributo](../media/as-icon-attribute.gif "icona di attributo")|Regular o AccountType|  
|![Icona di attributo chiave](../media/as-icon-key-attribute.gif "icona di attributo chiave")|Key|  
|![Icona di attributo padre](../media/as-icon-parent-attribute.gif "icona di attributo padre")|Parent|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alle proprietà degli attributi delle dimensioni](dimension-attribute-properties-reference.md)  
  
  