---
title: Interfaccia SQLXML | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7c67be98-efb5-446c-a0e3-ee67c43cb170
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2cb8975c4eda311b93c7a26c1d83eecbbfa581f4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlxml-interface"></a>Interfaccia SQLXML
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Con il driver JDBC viene fornito supporto per l'API di JDBC 4.0, in cui viene presentata l'interfaccia java.sql.SQLXML. Tale interfaccia definisce i metodi per interagire e modificare i dati XML. Il **SQLXML** esegue il mapping al tipo di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **xml** tipo di dati.  
  
 L'interfaccia SQLXML fornisce metodi per l'accesso al valore XML come un **stringa**, **lettore** o **Writer**, o come un **flusso**. Il valore XML è possibile accedere anche tramite un **origine** o impostare come un **risultato**, che vengono utilizzati per le API dei Parser XML, ad esempio modello DOM (Document Object), Simple API per XML (SAX) e Streaming API for XML (StAX), come anche come Trasforma con XSLT e XPath.  
  
## <a name="remarks"></a>Osservazioni  
 Nella tabella seguente sono descritti i metodi definiti nell'interfaccia SQLXML:  
  
|Sintassi del metodo|Descrizione del metodo|  
|-------------------|------------------------|  
|[Free (void)](http://go.microsoft.com/fwlink/?LinkId=131685)|Consente di liberare l'oggetto SQLXML e di rilasciare le risorse da questo bloccate.|  
|[InputStream getBinaryStream()](http://go.microsoft.com/fwlink/?LinkId=131754)|Restituisce un flusso di input per la lettura di dati da SQLXML.|  
|[Lettore getCharacterStream()](http://go.microsoft.com/fwlink/?LinkId=131755)|Restituisce il **XML** dati come oggetto java.IO. Reader o come un flusso di caratteri.|  
|[T estende getSource origine T (classe\<T > sourceClass)](http://go.microsoft.com/fwlink/?LinkId=131756)|Restituisce un **origine** per la lettura di **XML** valore specificato da questo **SQLXML** oggetto.<br /><br /> **Nota:** il metodo getSource supporta le seguenti origini: javax, saxsource, staxsource e. InputStream.|  
|[GetString (stringa)](http://go.microsoft.com/fwlink/?LinkId=131757)|Restituisce una rappresentazione di stringa del **XML** valore designato dall'oggetto SQLXML.|  
|[OutputStream setBinaryStream()](http://go.microsoft.com/fwlink/?LinkId=131758)|Recupera un flusso che può essere usato per scrivere il **XML** valore che rappresenta questo oggetto SQLXML.|  
|[Writer setCharacterStream()](http://go.microsoft.com/fwlink/?LinkId=131759)|Restituisce un flusso da utilizzare per scrivere il **XML** valore che rappresenta questo oggetto SQLXML.|  
|[T estende setResult risultato T (classe\<T > resultClass)](http://go.microsoft.com/fwlink/?LinkId=131760)|Restituisce un **risultato** per l'impostazione di **XML** valore specificato da questo **SQLXML** oggetto.<br /><br /> **Nota:** il metodo setResult supporta le seguenti origini: javax, SAXResult, staxresult e OutputStream.|  
|[setString(String value) void](http://go.microsoft.com/fwlink/?LinkId=131762)|Imposta il valore XML indicato dall'oggetto SQLXML specificata **stringa** rappresentazione.|  
  
 Le applicazioni possono leggere e scrivere valori XML da e in un oggetto SQLXML una sola volta.  
  
 Quando viene chiamato il metodo Free (), un oggetto SQLXML diventa non valido e non è né leggibile né scrivibile. Se l'applicazione tenta di richiamare un metodo su tale oggetto SQLXML diverso dal metodo Free (), viene generata un'eccezione.  
  
 L'oggetto SQLXML diventa né leggibile né scrivibile quando l'applicazione chiama uno dei seguenti metodi di richiamo: getSource getCharacterStream, getBinaryStream e getString.  
  
 L'oggetto SQLXML diventa leggibile né scrivibile quando l'applicazione chiama uno dei seguenti metodi di impostazione: setResult, setCharacterStream, setBinaryStream e setString.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di dati XML](../../connect/jdbc/supporting-xml-data.md)  
  
  
