---
title: _mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l
ms.date: 4/2/2020
api_name:
- _mbctohira
- _mbctohira_l
- _mbctokata
- _mbctokata_l
- _o__mbctohira
- _o__mbctohira_l
- _o__mbctokata
- _o__mbctokata_l
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbctokata
- mbctohira
- _mbctohira
- _mbctohira_l
- mbctokata
- mbctokata_l
- mbctohira_l
- _mbctokata_l
helpviewer_keywords:
- _mbctokata function
- _mbctokata_l function
- _mbctohira_l function
- mbctohira_l function
- mbctohira function
- mbctokata_l function
- _mbctohira function
- mbctokata function
ms.assetid: f949afd7-44d4-4f08-ac8f-1fef2c915a1c
ms.openlocfilehash: b5af94932fc90e6bcaee584e16f3056ee36dab51
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914381"
---
# <a name="_mbctohira-_mbctohira_l-_mbctokata-_mbctokata_l"></a>_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l

在平假名和片假名字符之间转换。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
unsigned int _mbctohira(
   unsigned int c
);
unsigned int _mbctohira_l(
   unsigned int c,
   _locale_t locale
);
unsigned int _mbctokata(
   unsigned int c
);
unsigned int _mbctokata_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*ansi-c*<br/>
要转换的多字节字符。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

如果可能，这些函数将返回转换后的字符*c*。 否则，它返回的字符*c*不变。

## <a name="remarks"></a>备注

**_Mbctohira**和 **_mbctokata**函数测试字符*c* ，如有可能，将应用以下转换之一。

|例程|转换|
|--------------|--------------|
|**_mbctohira**， **_mbctohira_l**|多字节片假名与多字节平假名。|
|**_mbctokata**， **_mbctokata_l**|多字节平假名与多字节片假名。|

输出值受区域设置的 LC_CTYPE 类别设置影响；有关详细信息，请参阅 [setlocale](setlocale-wsetlocale.md)****。 这些函数的版本相同，不同之处在于没有 **_l**后缀的函数会将当前区域设置用于与区域设置相关的行为，并且使用传入的区域设置参数 **_l**后缀。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

在早期版本中， **_mbctohira**命名为**jtohira** ， **_mbctokata**命名为**jtokata**。 对于新代码，请使用新名称。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_mbctohira**|\<mbstring.h>|
|**_mbctohira_l**|\<mbstring.h>|
|**_mbctokata**|\<mbstring.h>|
|**_mbctokata_l**|\<mbstring.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l](mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)<br/>
[_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l](mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)<br/>
[_mbctombb、_mbctombb_l](mbctombb-mbctombb-l.md)<br/>
