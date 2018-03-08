---
title: Creare un progetto Visual c# SMO in Visual Studio .NET | Documenti Microsoft
ms.custom: 
ms.date: 08/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: smo
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
caps.latest.revision: "43"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 220c190a88a1b5c5d38591905e9bb1060a2f4509
ms.sourcegitcommit: cb2f9d4db45bef37c04064a9493ac2c1d60f2c22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2018
---
# <a name="how-to-create-a-visual-c-smo-project-in-visual-studio-net"></a>Come creare un progetto Visual c# SMO in Visual Studio .NET
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  In questa sezione viene descritto come compilare un'applicazione console SMO semplice.  
  
 In questo esempio vengono importati spazi dei nomi affinché il programma faccia riferimento ai tipi SMO. L'importazione del **agente** dello spazio dei nomi è facoltativo. Utilizzarla quando si scrive un programma che utilizza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Il **comuni** dello spazio dei nomi è necessario per stabilire una connessione sicura per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il **SqlClient** dello spazio dei nomi viene utilizzato per elaborare gli errori di eccezione SQL.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Creazione di un progetto Visual C# SMO in Visual Studio.NET  
  
1. Avviare Visual Studio
  
2. Nel **File** menu, fare clic su **New** e quindi **progetto**.  Verrà visualizzata la finestra di dialogo **Nuovo progetto** .   
  
3. Nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **installato** riquadro, passare a **modelli**\\**Visual c#**\\**Windows** e selezionare **applicazione Console**.  
  
4. (Facoltativo) Nel **nome** testo, digitare il nome della nuova applicazione.  

5. Fare clic su **OK** per caricare il modello di applicazione console.  

6. Seguire le istruzioni in [l'installazione di SMO](installing-smo.md) per installare il pacchetto per il progetto fare riferimento.
  
7. Scegliere **Codice** dal menu **Visualizza**.
    
8. Nel codice, prima dell'istruzione dello spazio dei nomi, digitare quanto segue **utilizzando** istruzioni per qualificare i tipi nello spazio dei nomi SMO:
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
15. SMO dispone di vari spazi dei nomi in Microsoft.SqlServer.Management.Smo, ad esempio Microsoft.SqlServer.Management.Smo.Agent. Aggiungere questi spazi dei nomi poiché sono necessari.  
  
16. A questo punto è possibile aggiungere il codice SMO.  
  
  
