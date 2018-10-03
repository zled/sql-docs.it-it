---
title: Sintassi dei valori letterali numerica | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC literals [ODBC], numeric
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: fb17498d-4f1d-4b3d-b33d-1e62c7d3c32d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 18b1c144e84bf0be5aaeb68b66660f7bc7865ade
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601539"
---
# <a name="numeric-literal-syntax"></a>Sintassi dei valori letterali numerici
La sintassi seguente viene usata per i valori letterali numerici in ODBC:  
  
 *valore letterale numerico* :: = *letterali numerici firmati &#124; letterale numerico senza segno*  
  
 *letterali numerici firmato* :: = [*sign*] *letterale numerico senza segno*  
  
 *Unsigned-numerico-literal* :: = *letterale numerico esatto &#124; letterali numerici approssimati*  
  
 *valore esatto-numerico-literal* :: = *integer senza segno* [*periodo*[*unsigned integer*]]  *&#124;periodo unsigned integer*  
  
 *Sign* :: = *segno &#124; segno di sottrazione*  
  
 *letterali numerici approssimati* :: = *esponente mantissa E*  
  
 *mantissa* :: = *letterale numerico esatto*  
  
 *esponente* :: = *integer firmato*  
  
 *integer firmati* :: = [*sign*] *unsigned integer*  
  
 *intero senza segno* :: = *cifra...*  
  
 *segno di addizione* :: = *+*  
  
 *segno di sottrazione* :: = -  
  
 *cifra* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *periodo* :: =.
