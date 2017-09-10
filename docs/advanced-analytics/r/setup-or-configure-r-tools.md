---
title: Installare o configurare gli strumenti R | Microsoft Docs
ms.custom: 
ms.date: 01/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c04ae30-d391-4369-9742-d2b275e14c0d
caps.latest.revision: 9
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a3baf97a960d7e8f950bb6e9cd251550f4c4b942
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="setup-or-configure-r-tools"></a>Installare o configurare gli strumenti R
  Microsoft R Server fornisce tutte le librerie R di base, un set di pacchetti ScaleR e gli strumenti R standard necessari per sviluppare e testare il codice R. Se tuttavia si vuole usare un ambiente di sviluppo R dedicato, ce ne sono diversi disponibili, inclusi molti strumenti gratuiti.  
  
## <a name="basic-r-tools"></a>Strumenti R di base  
 Non sono necessari strumenti aggiuntivi in un'installazione di Microsoft R Server, perché tutti gli strumenti R standard inclusi in un'*installazione di base* di R vengono installati per impostazione predefinita.

-   **RTerm**: strumento da riga di comando per l'esecuzione di script R. 
  
-   **RGui.exe**: semplice editor interattivo per R. Gli argomenti della riga di comando sono gli stessi di RGui.exe e RTerm. 
  
-   **RScript**: strumento da riga di comando per l'esecuzione di script R in modalità batch.  

Per individuare questi strumenti, trovare il percorso della libreria R. Il percorso varia a seconda del fatto che sia installato solo SQL Server R Services o anche R Server (Standalone). Per altre informazioni, vedere [Che cosa viene installato e dove trovare i pacchetti R](https://msdn.microsoft.com/library/mt695941(sql.130).aspx#Anchor_1)

Cercare quindi nella cartella `..\R_SERVER\bin\x64`.  

> [!TIP]  
>  Sono necessarie informazioni per gli strumenti R? La documentazione è inclusa nella cartella di installazione, `C:\Program Files\Microsoft SQL Server\R_SERVER\doc`, e in `C:\Program Files\Microsoft SQL Server\R_SERVER\doc\manual`.  
>   
>  In alternativa, aprire **RGui**, fare clic sul collegamento alla**** Guida e selezionare una delle opzioni.  

## <a name="microsoft-r-client"></a>Microsoft R Client

Microsoft R Client è uno strumento che può essere scaricato gratuitamente e consente di sviluppare soluzioni R che possono essere eseguite facilmente in Microsoft R Server o in SQL Server R Services. Questa opzione è pensata per offrire ai data scientist che potrebbero non avere accesso a R Server (disponibile nella versione Enterprise Edition) una soluzione per lo sviluppo di soluzioni che usano ScaleR. 

Se si usa un ambiente di sviluppo R diverso, ad esempio R Tools per Visual Studio o RStudio, per usare ScaleR è necessario specificare l'uso di Microsoft R Client come eseguibile R. In questo modo, si avrà accesso completo al pacchetto RevoScaleR e ad altre funzionalità di Microsoft R Server, anche se le prestazioni saranno limitate.

È anche possibile usare gli strumenti disponibili in R Client, ad esempio RGui e RTerm, per eseguire script o scrivere ed eseguire codice R ad hoc.

[Installare Microsoft R Client](https://msdn.microsoft.com/microsoft-r/r-client-install)
  
##  <a name="bkmk_RTools"></a> R Tools per Visual Studio  

 Per motivi di praticità nell'uso dei database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è consigliabile usare [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] come ambiente di sviluppo. [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] è un componente aggiuntivo gratuito per Visual Studio che funziona in tutte le edizioni di Visual Studio. Visual Studio fornisce anche supporto per l'integrazione di Python e F#.  

 Per istruzioni sull'installazione, vedere [come installare gli strumenti R per Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation).

> [!TIP]
> Prima di installare eventuali nuovi pacchetti, verificare quale runtime R viene usato per impostazione predefinita. In caso contrario, potrebbe capitare di installare i nuovi pacchetti R in un percorso di libreria predefinito e non riuscire a trovarli da R Server.


## <a name="rstudio"></a>RStudio

Se si preferisce usare RStudio, sono necessari alcuni passaggi aggiuntivi per usare le librerie RevoScaleR:
- Installare Microsoft R Server o Microsoft R Client per ottenere le librerie e i pacchetti necessari.
- Aggiornare il percorso di R per usare il runtime di R Server.

Per altre informazioni, vedere [Configure Your IDE](https://msdn.microsoft.com/microsoft-r/r-client-get-started#step-2-configure-your-ide) (Configurare l'IDE).


## <a name="see-also"></a>Vedere anche  
 [Creare un server R autonomo](../../advanced-analytics/r-services/create-a-standalone-r-server.md)   
 [Introduzione a Microsoft R Server &#40;Standalone&#41;](../../advanced-analytics/r-services/getting-started-with-microsoft-r-server-standalone.md)  
  
  

