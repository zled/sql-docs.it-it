---
title: Sintassi del valore letterale numerica | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC literals [ODBC], numeric
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: fb17498d-4f1d-4b3d-b33d-1e62c7d3c32d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b6340f3ccbc3760a1e708d1f2e1d9832f3c2c3e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="numeric-literal-syntax"></a>Sintassi del valore letterale numerica
Per i valori letterali numerici in ODBC, viene utilizzata la sintassi seguente:  
  
 *valore letterale numerico* :: = *letterale numerico firmati &#124; letterale numerico senza segno*  
  
 *firma-numerico-literal* :: = [*sign*] *letterale numerico senza segno*  
  
 *Unsigned-numerico-literal* :: = *letterale numerico esatto &#124; Colony-numerico-literal*  
  
 *valore esatto-numerico-literal* :: = *intero senza segno* [*periodo*[*intero senza segno*]]  *&#124;periodo unsigned integer*  
  
 *Sign* :: = *segno &#124; meno (-)*  
  
 *Colony-numerico-literal* :: = *esponente mantissa E*  
  
 *mantissa* :: = *esatta-numerico-literal*  
  
 *esponente* :: = *integer firmato*  
  
 *valore integer firmato* :: = [*sign*] *intero senza segno*  
  
 *intero senza segno* :: = *cifra...*  
  
 *segno di addizione* :: = *+*  
  
 *segno di sottrazione* :: = -  
  
 *cifra* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *periodo* :: =.
