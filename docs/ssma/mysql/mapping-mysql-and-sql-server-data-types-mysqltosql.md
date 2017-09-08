---
title: Mapping di MySQL e SQL Server Data Types (MySQLToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Mapping, customize data type mapping
- Mapping, Type mapping
ms.assetid: 14f98054-13b4-4231-a6b0-2452f3b9941d
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3dd2adf0b8f6379bd11dc80de4cc2aedf5b3c102
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="mapping-mysql-and-sql-server-data-types-mysqltosql"></a>Mapping di tipi di dati (MySQLToSQL) di SQL Server e MySQL
Diversi tipi di database MySQL da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o tipi di database di SQL Azure. Quando si esegue la conversione di oggetti di database MySQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o oggetti di SQL Azure, è necessario specificare come eseguire il mapping dei tipi di dati da MySQL a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o SQL Azure. È possibile accettare i mapping dei tipi di dati predefinito oppure è possibile personalizzare i mapping, come illustrato nelle procedure seguenti.  
  
## <a name="default-mappings"></a>Mapping predefiniti  
SSMA è un set predefinito di mapping dei tipi di dati. Per l'elenco dei mapping predefiniti, vedere [impostazioni progetto &#40; Mapping dei tipi di &#41; &#40; MySQLToSQL &#41; ](../../ssma/mysql/project-settings-type-mapping-mysqltosql.md).  
  
## <a name="type-mapping-inheritance"></a>Mapping di ereditarietà dei tipi  
È possibile personalizzare i mapping dei tipi a livello di progetto, il livello di categoria oggetto (ad esempio, tutte le stored procedure) o livello di oggetto. Le impostazioni vengono ereditate da un livello più alto, a meno che vengano sostituiti con un livello inferiore. Ad esempio, se si esegue il mapping **smallint** a **int** a livello di progetto, tutti gli oggetti nel progetto utilizzerà questo mapping, a meno che per personalizzare il mapping a livello di oggetto o alla categoria.  
  
Quando si visualizza il **del mapping dei tipi** scheda SSMA, lo sfondo è contraddistinte da colore per mostrare il mapping dei tipi vengono ereditati. Lo sfondo di un mapping dei tipi è giallo per il mapping dei tipi ereditati e bianco per qualsiasi mapping specificato al livello corrente.  
  
## <a name="customizing-data-type-mappings"></a>Personalizzazione dei mapping dei tipi di dati  
  
-   **Eseguire il mapping di tipi di dati:**  
  
    Le procedure seguenti illustrano come eseguire il mapping di tipi di dati nel progetto, database o il livello di oggetto di database:  
  
    1.  Per personalizzare i mapping dei tipi di dati per l'intero progetto, aprire il **impostazioni progetto** la finestra di dialogo. Dal menu Strumenti, selezionare **impostazioni progetto**.  
  
        Nel riquadro a sinistra, selezionare **del mapping dei tipi**. Il grafico di mapping di tipo e i pulsanti vengono visualizzati nel riquadro di destra.  
  
    2.  Per personalizzare i mapping dei tipi di dati a livello di database o tabella, selezionare il database o la tabella in Visualizzatore metadati MySQL. Nel Visualizzatore metadati MySQL, selezionare la cartella o oggetto da personalizzare.  
  
        Nel riquadro di destra, fare clic su **del mapping dei tipi**.  
  
-   **Per aggiungere un nuovo mapping, eseguire le operazioni seguenti:**  
  
    1.  Nel riquadro del mapping dei tipi, fare clic su **Aggiungi** .  
  
    2.  Nel nuovo tipo di finestra di dialogo Mapping, in **tipo di origine**, selezionare il tipo di dati di MySQL per eseguire il mapping.  
  
    3.  Se il tipo richiede una lunghezza, specificare le lunghezze di dati minimo e massimo per il mapping selezionando il **da** e **per** le caselle di controllo e quindi immettere i valori.  
  
    4.  Ciò consente di personalizzare il mapping dei dati per i valori di dimensioni minori e più grandi dello stesso tipo di dati. In **tipo di destinazione**, selezionare la destinazione SQL Server o un tipo di dati di SQL Azure.  
  
        1.  Alcuni tipi richiedono una lunghezza di tipo di dati di destinazione. Se richiesto, immettere la nuova lunghezza dei dati nel **Sostituisci con** casella e quindi fare clic su **OK**.  
  
        2.  Alcuni tipi richiedono un tipo di dati di destinazione **precisione** e **scala**. Se richiesto, immettere la nuova precisione e scala nel **Sostituisci con** casella e quindi fare clic su **OK**.  
  
-   **Per modificare un mapping dei tipi, eseguire le operazioni seguenti:**  
  
    1.  Nel riquadro del mapping dei tipi, fare clic su **modifica**.  
  
    2.  Nel Mapping di tipo elenco nella finestra di dialogo in **tipo di origine**, selezionare il tipo di dati di MySQL per eseguire il mapping.  
  
    3.  Se il tipo richiede una lunghezza, specificare le lunghezze di dati minimo e massimo per il mapping selezionando il **da** e **per** le caselle di controllo e quindi immettere i valori.  
  
    Ciò consente di personalizzare il mapping dei dati per i valori di dimensioni minori e più grandi dello stesso tipo di dati. In **tipo di destinazione**, selezionare la destinazione SQL Server o un tipo di dati di SQL Azure.  
  
    1.  Alcuni tipi richiedono una lunghezza di tipo di dati di destinazione. Se richiesto, immettere la nuova lunghezza dei dati nel **Sostituisci con** casella e quindi fare clic su **OK**.  
  
    2.  Alcuni tipi richiedono un tipo di dati di destinazione **precisione** e **scala** . Se richiesto, immettere la nuova precisione e scala nel **Sostituisci con** casella e quindi fare clic su **OK** .  
  
-   **Per rimuovere un mapping dei tipi di dati, eseguire le operazioni seguenti:**  
  
    1.  Nel riquadro di Mapping dei tipi, selezionare la riga nell'elenco di mapping di tipo che contiene il mapping dei tipi di dati che si desidera rimuovere.  
  
    2.  Scegliere **Rimuovi**.  
  
## <a name="next-step"></a>Passaggio successivo  
Il passaggio successivo del processo di migrazione è su [creare una relazione di valutazione](http://msdn.microsoft.com/en-us/2a56a003-3b0f-453a-963c-00c9e40933ec) o [MySQL convertire gli oggetti di database in SQL Server o SQL Azure sintassi](http://msdn.microsoft.com/en-us/ac21850b-fb32-4704-9985-5759b7c688c7). Se si crea un report, gli oggetti di MySQL vengono convertiti automaticamente durante la valutazione.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database MySQL a SQL Server: database SQL di Azure &#40; MySQLToSql &#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  

