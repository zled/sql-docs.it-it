---
title: Interfaccia SQLXML | Microsoft Docs
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
ms.openlocfilehash: 50e80b34becde8987a06f9293a39ba24e3639cd2
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/02/2018
ms.locfileid: "39454195"
---
# <a name="sqlxml-interface"></a>Interfaccia SQLXML

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Con il driver JDBC viene fornito supporto per l'API di JDBC 4.0, in cui viene presentata l'interfaccia java.sql.SQLXML. Tale interfaccia definisce i metodi per interagire e modificare i dati XML. Il **SQLXML** esegue il mapping al tipo di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **xml** tipo di dati.  
  
L'interfaccia SQLXML fornisce i metodi per l'accesso al valore XML come un **stringa**, un **lettore** oppure **Writer**, oppure come un **Stream**. È inoltre possibile accedere al valore XML tramite **Origine** oppure impostarlo come **Risultato**, utilizzati con le API dei parser XML, tra cui Document Object Model (DOM), Simple API for XML (SAX) e Streaming API for XML (StAX), nonché con trasformazioni XSLT e XPath.  
  
## <a name="remarks"></a>Remarks  

Nella tabella seguente sono descritti i metodi definiti nell'interfaccia SQLXML:  
  
|Sintassi del metodo|Descrizione del metodo|  
|-------------------|------------------------|  
|[void free()](http://go.microsoft.com/fwlink/?LinkId=131685)|Consente di liberare l'oggetto SQLXML e di rilasciare le risorse da questo bloccate.|  
|[InputStream getBinaryStream()](http://go.microsoft.com/fwlink/?LinkId=131754)|Restituisce un flusso di input per la lettura di dati da SQLXML.|  
|[Reader getCharacterStream()](http://go.microsoft.com/fwlink/?LinkId=131755)|Restituisce i dati **XML** come oggetto java.io.Reader o come flusso di caratteri.|  
|[T estende getSource origine T (classe\<T > sourceClass)](http://go.microsoft.com/fwlink/?LinkId=131756)|Restituisce un **origine** per la lettura di **XML** valore specificato da questo **SQLXML** oggetto.<br /><br /> **Nota:** Il metodo getSource supporta le seguenti origini: javax.xml.transform.dom.DOMSource, javax.xml.transform.sax.SAXSource, javax.xml.transform.stax.StAXSource e java.io.InputStream.|  
|[String getString()](http://go.microsoft.com/fwlink/?LinkId=131757)|Restituisce una rappresentazione di stringa del valore **XML** indicato dall'oggetto SQLXML.|  
|[OutputStream setBinaryStream()](http://go.microsoft.com/fwlink/?LinkId=131758)|Recupera un flusso che può essere utilizzato per scrivere il valore **XML** rappresentato dall'oggetto SQLXML.|  
|[Writer setCharacterStream()](http://go.microsoft.com/fwlink/?LinkId=131759)|Restituisce un flusso da utilizzare per scrivere il valore **XML** rappresentato dall'oggetto SQLXML.|  
|[T estende setResult risultato T (classe\<T > resultClass)](http://go.microsoft.com/fwlink/?LinkId=131760)|Restituisce un **risultato** per l'impostazione di **XML** valore specificato da questo **SQLXML** oggetto.<br /><br /> **Nota:** Il metodo setResult supporta le seguenti origini: javax.xml.transform.dom.DOMResult, javax.xml.transform.sax.SAXResult, javax.xml.transform.stax.StaxResult e java.io.OutputStream.|  
|[void setString(String value)](http://go.microsoft.com/fwlink/?LinkId=131762)|Imposta il valore XML indicato dall'oggetto SQLXML sulla rappresentazione **Stringa** specificata.|  
  
Le applicazioni possono leggere e scrivere valori XML da e in un oggetto SQLXML una sola volta.  
  
Quando viene chiamato il metodo free(), un oggetto SQLXML diventa non valido e non è accessibile in lettura o scrittura. Se l'applicazione tenta di richiamare su tale oggetto SQLXML un metodo diverso da free(), verrà generata un'eccezione.  
  
L'oggetto SQLXML diventa né leggibile né modificabile quando l'applicazione chiama uno dei seguenti metodi di richiamo: getSource, getCharacterStream, getBinaryStream, getString e.  
  
L'oggetto SQLXML diventa inaccessibile in lettura o quando l'applicazione chiama uno dei seguenti metodi di impostazione: setResult, setCharacterStream, setBinaryStream e setString.  
  
## <a name="see-also"></a>Vedere anche  

[Supporto di dati XML](../../connect/jdbc/supporting-xml-data.md)  
