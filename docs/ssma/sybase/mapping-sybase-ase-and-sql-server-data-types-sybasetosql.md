---
title: Mapping di Sybase ASE e tipi di dati SQL Server (SybaseToSQL) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Mapping Sybase ASE Schemas to SQL Server Schemas
- Type Mapping Settings
ms.assetid: 784365d3-df4e-47ab-8ee0-d8392b52f510
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cca6fecaee64c828d94bb8f72c3caf2aae3273b6
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="mapping-sybase-ase-and-sql-server-data-types-sybasetosql"></a>Mapping di Sybase ASE e tipi di dati SQL Server (SybaseToSQL)
Tipi di database di Sybase Adaptive Server Enterprise (ASE) diversi da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o tipi di database di SQL Azure. Quando si esegue la conversione di oggetti di database ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o oggetti di SQL Azure, è necessario specificare come eseguire il mapping di tipi di dati di base per [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. È possibile accettare i mapping dei tipi di dati predefinito oppure è possibile personalizzare i mapping, come illustrato nelle sezioni seguenti.  
  
## <a name="default-mappings"></a>Mapping predefiniti  
SSMA è un set predefinito di mapping dei tipi di dati. Per l'elenco di mapping predefiniti, vedere [impostazioni del progetto di &#40;Mapping dei tipi&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md).  
  
## <a name="type-mapping-inheritance"></a>Mapping di ereditarietà dei tipi  
È possibile personalizzare i mapping dei tipi a livello di progetto, il livello di categoria oggetto (ad esempio, tutte le stored procedure) o livello di oggetto. Impostazioni vengono ereditate da un livello più alto, a meno che non viene sottoposto a override con un livello inferiore. Ad esempio, se si esegue il mapping **smallmoney** a **money** a livello di progetti, tutti gli oggetti nel progetto utilizzerà questo mapping, a meno che per personalizzare il mapping a livello di oggetto o il livello di categoria dell'oggetto.  
  
Quando si visualizza il **del mapping dei tipi** scheda SSMA, lo sfondo è contraddistinte da colore per mostrare il mapping dei tipi vengono ereditati. Lo sfondo di un mapping dei tipi è giallo per il mapping dei tipi ereditati e bianco per qualsiasi mapping specificato al livello corrente.  
  
## <a name="customizing-data-type-mappings"></a>Personalizzazione dei mapping dei tipi di dati  
La procedura seguente viene illustrato come eseguire il mapping di tipi di dati nel progetto, database o il livello di oggetto.  
  
**Eseguire il mapping di tipi di dati**  
  
1.  Per personalizzare i mapping dei tipi di dati per l'intero progetto, aprire il **impostazioni progetto** la finestra di dialogo:  
  
    1.  Nel **strumenti** dal menu **impostazioni progetto**.  
  
    2.  Nel riquadro a sinistra, selezionare **del mapping dei tipi**.  
  
        Il grafico di mapping di tipo e i pulsanti vengono visualizzati nel riquadro di destra.  
  
    In alternativa, per personalizzare il tipo di dati mapping a livello di database, tabella, vista o stored procedure, selezionare il database, la categoria dell'oggetto oppure l'oggetto in Visualizzatore metadati Sybase:  
  
    1.  In Visualizzatore metadati Sybase, selezionare la cartella o un oggetto che si desidera personalizzare.  
  
    2.  Nel riquadro di destra, fare clic su di **del mapping dei tipi** scheda.  
  
2.  Per aggiungere un nuovo mapping, eseguire le operazioni seguenti:  
  
    1.  Scegliere **Aggiungi**.  
  
    2.  In **tipo di origine**, selezionare il tipo di dati di base per eseguire il mapping.  
  
    3.  Se il tipo richiede una lunghezza, specificare la lunghezza minima di dati per il mapping nel **da** e specificare la lunghezza massima dei dati per il mapping nel **a** casella.  
  
        Ciò consente di personalizzare il mapping dei dati per i valori di dimensioni minori e più grandi dello stesso tipo di dati.  
  
    4.  In **tipo di destinazione**, selezionare la destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o il tipo di dati di SQL Azure.  
  
        Alcuni tipi richiedono una lunghezza di tipo di dati di destinazione. Se necessario, immettere la nuova lunghezza dei dati nel **sostituire** casella.  
  
    5.  Scegliere **OK**.  
  
3.  Per modificare un mapping dei tipi di dati, eseguire le operazioni seguenti:  
  
    1.  Fare clic su **Modifica**.  
  
    2.  In **tipo di origine**, selezionare il tipo di dati di base per eseguire il mapping.  
  
    3.  Se il tipo richiede una lunghezza, specificare la lunghezza minima di dati per il mapping nel **da** e specificare la lunghezza massima dei dati per il mapping nel **a** casella.  
  
        Ciò consente di personalizzare il mapping dei dati per i valori di dimensioni minori e più grandi dello stesso tipo di dati.  
  
    4.  In **tipo di destinazione**, selezionare la destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o il tipo di dati di SQL Azure.  
  
        Alcuni tipi richiedono una lunghezza di tipo di dati di destinazione. Se necessario, immettere la nuova lunghezza dei dati nel **sostituire con** casella e quindi fare clic su **OK**.  
  
4.  Per rimuovere un mapping dei tipi di dati personalizzati, effettuare le operazioni seguenti:  
  
    1.  Selezionare la riga nell'elenco di mapping di tipo che contiene il mapping dei tipi di dati che si desidera rimuovere.  
  
    2.  Scegliere **Rimuovi**.  
  
        È possibile rimuovere i mapping ereditati. Tuttavia, i mapping ereditati vengono sovrascritte dai mapping personalizzati in un oggetto specifico o una categoria dell'oggetto.  
  
## <a name="next-steps"></a>Passaggi successivi  
Il passaggio successivo del processo di migrazione è su [creare una relazione di valutazione](http://msdn.microsoft.com/en-us/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c) o [oggetti di database Sybase ASE convertire la sintassi di SQL Server o SQL Azure](http://msdn.microsoft.com/en-us/509cb65d-2f54-427a-83d7-37919cc4e3e3). Se si crea una relazione di valutazione, gli oggetti di Sybase ASE vengono convertiti automaticamente durante la valutazione.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database Sybase ASE a SQL Server: SQL Azure database &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
