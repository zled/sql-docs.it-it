---
title: Le impostazioni di conversione (MySQLToSQL) | Documenti Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: f551cf6e-1575-4206-9cca-975b5b43a6b8
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9284ccc7adab73068bc615bf6f294a23c59c42cf
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="conversion-settings-mysqltosql"></a>Impostazioni di conversione (MySQLToSQL)
Il **'Impostazioni'** scheda consente di impostare le impostazioni a livello di nodo. La scheda è disponibile in nodi Metabase seguenti:  
  
-   Nodo del database  
  
-   Categoria di funzioni  
  
-   Nodo (funzione)  
  
-   Categoria di tabelle  
  
-   Nodo della tabella  
  
## <a name="specifications"></a>Specifiche:  
Il **impostazioni** scheda sono presenti due impostazioni utente, dei quali.:  
  
1.  Conversione (funzione)  
  
2.  Conversione della tabella  
  
Queste impostazioni saranno disponibili in base al tipo di nodo della Metabase. Ad esempio, funzione di conversione correlati impostazione non sarà disponibile in corrispondenza del nodo di tabella  
  
> [!NOTE]  
> -   Le modifiche apportate dall'utente verranno essere salvate come file separato preferenza nell'area di lavoro di progetto.  
> -   L'estensione di questo file sarà **ccprefs**.  
  
1.  **Impostazione di conversione (funzione):**  
  
    1.  Questa scheda contiene **'Forzare la conversione di funzione'** opzione. L'opzione può avere uno dei quattro valori seguenti:  
  
        -   Convertire in base alle impostazioni di progetto [ereditate]  
  
        -   Sempre la conversione a una funzione  
  
        -   Converte sempre in una stored Procedure  
  
        -   Convertire in base alle impostazioni di progetto  
  
    2.  In base alle impostazioni, la funzione verrà convertita in una funzione o a una stored procedure.  
  
    3.  Le impostazioni apportate dall'utente vengono salvate nel file delle preferenze in serie fare clic su **applica** pulsante.  
  
2.  **Impostazione di conversione tabella:**  
  
    1.  Questa scheda contiene **'Generazione colonna ausiliario esclusione ROWID'** opzione. L'opzione può avere uno dei quattro valori seguenti:  
  
        -   Convertire in base alle impostazioni di progetto [ereditate]  
  
        -   Sì  
  
        -   no  
  
        -   Convertire in base alle impostazioni di progetto  
  
    2.  Se **'Sì'**, questa impostazione impedisce la creazione della creazione di colonna ausiliario ROWID nelle tabelle di destinazione.  
  
    3.  Le impostazioni apportate dall'utente vengono salvate nel file di preferenze in serie fare clic su **applica** pulsante.  
  
## <a name="see-also"></a>Vedere anche  
[Impostazioni del progetto (conversione) (MySQL to SQL)](http://msdn.microsoft.com/en-us/7ad5fe44-6445-4ba8-a457-5af792631f11)  
  
