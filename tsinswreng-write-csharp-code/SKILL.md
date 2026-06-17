---

name: write-csharp-code

description: 編寫C#代碼時閱讀此skill

---

## 類型別名

```cs
global using i32 = int;
global using str = string;
global using obj = object;
global using nil = object; // 專門用來表示null
global using CT = CancellationToken;
```

全局變量:`const nil NIL = null`

## 異步函數規範

- 約定 最後一個參數聲明爲`CT Ct`的爲異步函數、不需要加`Async後綴`
- 異步函數不返回值時、返回值聲明爲`Task<nil>`、不用無泛型的Task
- 異步函數實現(有方法體的即函數實現)一定要加`async`

正確示例:

```cs
async Task<nil> WriteToFile(str FilePath, str Content, CT Ct){
	...
	return NIL;
}
```

## 代碼風格

- 左大括號不換行
- 除函數中的局部變量外、所有標識符(包括函數參數)都用大駝峯! 首字母要大寫!

## AOT

除非特殊說明、 **!!!所有代碼必須兼容AOT!!!**

- 禁止使用一切不兼容AOT的反射, Emit等
- 禁止在表達式樹外使用匿名對象
- 禁止使用dynamic
