---
title: Utilizzo di un'istruzione SQL per modificare i dati | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4704199b-c0ae-4c77-8a2e-6963715b4ffb
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 750e91c909e859d5d1e3d2bf15b5e0bf4cc11db1
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662433"
---
# <a name="using-an-sql-statement-to-modify-data"></a>Utilizzo di un'istruzione SQL per modificare i dati

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Per modificare i dati contenuti in un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] usando un'istruzione SQL, è possibile usare il metodo [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) della classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Con il metodo executeUpdate l'istruzione SQL viene passata al database per l'elaborazione e viene restituito un valore che indica il numero di righe modificate.

A tale scopo, è necessario innanzitutto creare un oggetto SQLServerStatement usando il metodo [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) della classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

Nell'esempio seguente, viene passata alla funzione una connessione aperta al database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], viene costruita un'istruzione SQL che aggiunge nuovi dati alla tabella, viene eseguita l'istruzione e viene visualizzato il valore restituito.

[!code[JDBC#UsingSQLToModifyData1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_1_1.java)]

> [!NOTE]  
> Per usare un'istruzione SQL contenente dei parametri per la modifica dei dati contenuti in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è consigliabile usare il metodo [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md) della classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).
>
> Se nella colonna in cui si desidera inserire i dati sono presenti caratteri speciali, quali, ad esempio, gli spazi, è necessario fornire i valori da inserire, anche se si tratta dei valori predefiniti. In caso contrario, l'operazione di inserimento non verrà eseguita correttamente.
>
> Se si desidera che il driver JDBC restituisca tutti i conteggi degli aggiornamenti, inclusi i conteggi degli aggiornamenti restituiti dai trigger eventualmente attivati, impostare la proprietà della stringa di connessione lastUpdateCount su "false". Per altre informazioni sulla proprietà lastUpdateCount, vedere [impostazione delle proprietà di connessione](../../connect/jdbc/setting-the-connection-properties.md).

## <a name="see-also"></a>Vedere anche

[Uso di istruzioni con SQL](../../connect/jdbc/using-statements-with-sql.md)
