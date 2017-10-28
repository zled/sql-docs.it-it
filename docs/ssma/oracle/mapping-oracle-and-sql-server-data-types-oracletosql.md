---
title: Mapping di Oracle e tipi di dati SQL Server (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Type Mapping Inheritance
ms.assetid: 05da1495-63b9-47b7-86e2-6746394a2d8a
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 400ed2a28e622ffb9493af7462e06f551a214a51
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="mapping-oracle-and-sql-server-data-types-oracletosql"></a>Mapping di Oracle e tipi di dati SQL Server (OracleToSQL)
Diversi tipi di database Oracle da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di database. Quando si esegue la conversione di oggetti di database Oracle [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti, è necessario specificare come eseguire il mapping dei tipi di dati da Oracle a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È possibile accettare i mapping dei tipi di dati predefinito oppure è possibile personalizzare i mapping, come illustrato nelle sezioni seguenti.  
  
## <a name="default-mappings"></a>Mapping predefiniti  
SSMA è un set predefinito di mapping dei tipi di dati. Per l'elenco dei mapping predefiniti, vedere [impostazioni progetto &#40; Mapping dei tipi di &#41; &#40; OracleToSQL &#41; ](../../ssma/oracle/project-settings-type-mapping-oracletosql.md).  
  
## <a name="type-mapping-inheritance"></a>Mapping di ereditarietà dei tipi  
È possibile personalizzare i mapping dei tipi a livello di progetto, il livello di categoria oggetto (ad esempio, tutte le stored procedure) o livello di oggetto. Le impostazioni vengono ereditate da un livello più alto, a meno che vengano sostituiti con un livello inferiore. Ad esempio, se si esegue il mapping **smallmoney** a **money** a livello di progetto, tutti gli oggetti nel progetto utilizzerà questo mapping, a meno che per personalizzare il mapping a livello di oggetto o alla categoria.  
  
Quando si visualizza il **del mapping dei tipi** scheda SSMA, lo sfondo è contraddistinte da colore per mostrare il mapping dei tipi vengono ereditati. Lo sfondo di un mapping dei tipi è giallo per il mapping dei tipi ereditati e bianco per qualsiasi mapping specificato al livello corrente.  
  
## <a name="customizing-data-type-mappings"></a>Personalizzazione dei mapping dei tipi di dati  
La procedura seguente viene illustrato come eseguire il mapping di tipi di dati nel progetto, database o il livello di oggetto:  
  
**Per eseguire il mapping di tipi di dati**  
  
1.  Per personalizzare i mapping dei tipi di dati per l'intero progetto, aprire il **impostazioni progetto** la finestra di dialogo:  
  
    1.  Nel **strumenti** dal menu **impostazioni progetto**.  
  
    2.  Nel riquadro a sinistra, selezionare **del mapping dei tipi**.  
  
        Il grafico di mapping di tipo e i pulsanti vengono visualizzati nel riquadro di destra.  
  
    In alternativa, per personalizzare il tipo di dati mapping a livello di database, tabella, vista o stored procedure, selezionare il database, la categoria dell'oggetto oppure l'oggetto in Visualizzatore metadati Oracle:  
  
    1.  Nel Visualizzatore metadati Oracle, selezionare la cartella o oggetto da personalizzare.  
  
    2.  Nel riquadro di destra, fare clic su di **del mapping dei tipi** scheda.  
  
2.  Per aggiungere un nuovo mapping, eseguire le operazioni seguenti:  
  
    1.  Scegliere **Aggiungi**.  
  
    2.  In **tipo di origine**, selezionare il tipo di dati Oracle per eseguire il mapping.  
  
    3.  Se il tipo richiede una lunghezza, specificare la lunghezza minima di dati per il mapping nel **da** casella e la lunghezza massima dei dati nel **a** casella.  
  
        Ciò consente di personalizzare il mapping dei dati per i valori di dimensioni minori e più grandi dello stesso tipo di dati.  
  
    4.  In **tipo di destinazione**, selezionare la destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo di dati.  
  
        Alcuni tipi richiedono una lunghezza di tipo di dati di destinazione. Se necessario, immettere la nuova lunghezza dei dati nel **sostituire** casella.  
  
    5.  [!INCLUDE[clickOK](../../includes/clickok_md.md)]  
  
3.  Per modificare un mapping dei tipi di dati, eseguire le operazioni seguenti:  
  
    1.  Fare clic su **Modifica**.  
  
    2.  In **tipo di origine**, selezionare il tipo di dati Oracle per eseguire il mapping.  
  
    3.  Se il tipo richiede una lunghezza, specificare la lunghezza minima di dati per il mapping nel **da** casella e la lunghezza massima dei dati nel **a** casella.  
  
        Ciò consente di personalizzare il mapping dei dati per i valori di dimensioni minori e più grandi dello stesso tipo di dati.  
  
    4.  In **tipo di destinazione**, selezionare la destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo di dati.  
  
        Alcuni tipi richiedono una lunghezza di tipo di dati di destinazione. Se necessario, immettere la nuova lunghezza dei dati nel **sostituire** casella, quindi[!INCLUDE[clickOK](../../includes/clickok_md.md)]  
  
4.  Per rimuovere un mapping dei tipi di dati personalizzati, effettuare le operazioni seguenti:  
  
    1.  Selezionare la riga nell'elenco di mapping di tipo che contiene il mapping dei tipi di dati che si desidera rimuovere.  
  
    2.  Scegliere **Rimuovi**.  
  
        È possibile rimuovere i mapping ereditati. Tuttavia, i mapping ereditati vengono sovrascritte dai mapping personalizzati in un oggetto specifico o una categoria dell'oggetto.  
  
## <a name="next-steps"></a>Passaggi successivi  
Il passaggio successivo del processo di migrazione è su [creare una relazione di valutazione](http://msdn.microsoft.com/en-us/4de9bcf6-1346-4740-87f9-7f24a8226357) o [convertire gli oggetti di database Oracle in sintassi SQL Server](http://msdn.microsoft.com/en-us/e021182d-31da-443d-b110-937f5db27272). Se si crea una relazione di valutazione, oggetti Oracle vengono convertiti automaticamente durante la valutazione.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database Oracle a SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  

