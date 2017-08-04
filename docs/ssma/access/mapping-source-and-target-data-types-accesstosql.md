---
title: Mapping di origine e i tipi di dati di destinazione (AccessToSQL) | Documenti Microsoft
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
- customizing data type mappings
- data types, mapping
- mapping, data types
- source data types
- target data types
ms.assetid: b362a075-16e7-423f-b63f-e1e9f02844a9
caps.latest.revision: 14
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 95783265e2e89df6aeafbbe0d74e6d999cbdcff3
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="mapping-source-and-target-data-types-accesstosql"></a>Mapping di origine e i tipi di dati di destinazione (AccessToSQL)
Diversi tipi di database di Access da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipi di database. Quando si esegue la conversione di oggetti di database di Access da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] oggetti, è necessario specificare come eseguire il mapping dei tipi di dati dall'accesso al [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. È possibile accettare i mapping dei tipi di dati predefinito oppure è possibile personalizzare i mapping, come illustrato nelle procedure seguenti.  
  
## <a name="default-mappings"></a>Mapping predefiniti  
SSMA è un set predefinito di mapping dei tipi di dati. Per l'elenco dei mapping predefiniti, vedere [le impostazioni di progetto (tipo di Mapping)](http://msdn.microsoft.com/en-us/b87b9683-abed-4677-8c50-18bdba704655).  
  
## <a name="customizing-data-type-mappings"></a>Personalizzazione dei mapping dei tipi di dati  
Tramite il **impostazioni progetto** nella finestra di dialogo è possibile personalizzare la modalità di mapping dei tipi per tutti i database e oggetti di database in un progetto. I mapping dei tipi per un progetto si applicano a tutti i database e oggetti di database che non dispongono di mapping dei tipi personalizzati.  
  
È inoltre possibile personalizzare i mapping dei tipi di dati a livello di database o tabella.  
  
La procedura seguente viene illustrato come eseguire il mapping di tipi di dati nel progetto, database o il livello di oggetto di database.  
  
**Per eseguire il mapping di tipi di dati**  
  
1.  Per personalizzare i mapping dei tipi di dati per l'intero progetto, aprire il **impostazioni progetto** la finestra di dialogo:  
  
    1.  Nel **strumenti** dal menu **impostazioni progetto**.  
  
    2.  Nel riquadro a sinistra, selezionare **del mapping dei tipi**.  
  
        Il grafico di mapping di tipo e i pulsanti vengono visualizzati nel riquadro di destra.  
  
    In alternativa, per personalizzare i mapping dei tipi di dati a livello di database o tabella, selezionare il database o una tabella nel riquadro di esplorazione dei metadati di accesso:  
  
    1.  Nel riquadro Visualizzatore metadati accesso espandere **accesso metabase**, quindi espandere **database**.  
  
    2.  Selezionare il database o tabella per cui si desidera personalizzare il mapping dei tipi di dati.  
  
    3.  Nel riquadro di destra, fare clic su **del mapping dei tipi**.  
  
2.  Per aggiungere un nuovo mapping, eseguire le operazioni seguenti:  
  
    1.  Nel riquadro del mapping dei tipi, fare clic su **Aggiungi**.  
  
    2.  Nel **nuovo Mapping dei tipi** nella finestra di dialogo **tipo di origine**, selezionare il tipo di dati di accesso per eseguire il mapping.  
  
    3.  Se il tipo richiede una lunghezza, specificare le lunghezze di dati minimo e massimo per il mapping selezionando il **da** e **per** le caselle di controllo e quindi immettere i valori.  
  
        Ciò consente di personalizzare il mapping dei dati per i valori di dimensioni minori e più grandi dello stesso tipo di dati.  
  
    4.  In **tipo di destinazione**, selezionare la destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo di dati.  
  
        Alcuni tipi richiedono una lunghezza di tipo di dati di destinazione. Se necessario, immettere la nuova lunghezza dei dati nel **Sostituisci con** casella e quindi fare clic su **OK**.  
  
3.  Per modificare un mapping dei tipi di dati, eseguire le operazioni seguenti:  
  
    1.  Nel riquadro del mapping dei tipi, fare clic su **modifica**.  
  
    2.  Nel **elenco di Mapping di tipo** nella finestra di dialogo **tipo di origine**, selezionare il tipo di dati di accesso per eseguire il mapping.  
  
    3.  Se il tipo richiede una lunghezza, specificare le lunghezze di dati minimo e massimo per il mapping selezionando il **da** e **per** le caselle di controllo e quindi immettere i valori.  
  
        Ciò consente di personalizzare il mapping dei dati per i valori di dimensioni minori e più grandi dello stesso tipo di dati.  
  
    4.  In **tipo di destinazione**, selezionare la destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] tipo di dati.  
  
        Alcuni tipi richiedono una lunghezza di tipo di dati di destinazione. Se necessario, immettere la nuova lunghezza dei dati nel **Sostituisci con** casella e quindi fare clic su **OK**.  
  
4.  Per rimuovere un mapping dei tipi di dati, eseguire le operazioni seguenti:  
  
    1.  Nel riquadro di Mapping dei tipi, selezionare la riga nell'elenco di mapping di tipo che contiene il mapping dei tipi di dati che si desidera rimuovere.  
  
    2.  Scegliere **Rimuovi**.  
  
## <a name="next-steps"></a>Passaggi successivi  
Il passaggio successivo del processo di migrazione è [convertire gli oggetti di database di accesso agli oggetti di SQL Server](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione di database di Access a SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  

